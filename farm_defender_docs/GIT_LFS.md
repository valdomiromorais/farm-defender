# Configuração do Git LFS para o Projeto Farm Defender

## O que é Git LFS?

Git Large File Storage (LFS) é uma extensão do Git que permite trabalhar com arquivos grandes de forma eficiente. Em vez de armazenar o conteúdo completo dos arquivos grandes no repositório Git, o Git LFS armazena apenas referências a esses arquivos, enquanto o conteúdo real é armazenado em um servidor separado.

Isso é especialmente útil para projetos de jogos como o Farm Defender, que incluem:
- Modelos 3D (.blend, .fbx, .obj)
- Texturas e imagens de alta resolução
- Arquivos de áudio e vídeo
- Arquivos específicos do Unity

## Instalação do Git LFS

### Windows

1. Baixe o instalador do Git LFS em: https://git-lfs.github.com/
2. Execute o instalador e siga as instruções
3. Abra o PowerShell ou CMD e execute:
   ```
   git lfs install
   ```

### macOS (usando Homebrew)

```
brew install git-lfs
git lfs install
```

### Linux (Ubuntu/Debian)

```
sudo apt-get install git-lfs
git lfs install
```

## Configuração já realizada no projeto

O arquivo `.gitattributes` já foi configurado na raiz do projeto para rastrear automaticamente os seguintes tipos de arquivos usando Git LFS:

- Arquivos de modelo 3D (.blend, .fbx, .obj, etc.)
- Texturas e imagens (.png, .jpg, .psd, etc.)
- Arquivos de áudio (.mp3, .wav, .ogg)
- Arquivos de vídeo (.mp4, .mov)
- Arquivos específicos do Unity (.unitypackage, .asset, .unity)
- Arquivos compactados (.zip, .rar, .7z)
- Documentos grandes (.pdf)

## Como usar o Git LFS no projeto

### Verificar status do Git LFS

Para verificar quais arquivos estão sendo rastreados pelo Git LFS:

```
git lfs status
```

### Rastrear novos tipos de arquivo

Se precisar adicionar um novo tipo de arquivo para ser rastreado pelo Git LFS:

```
git lfs track "*.extensao"
```

Isso adicionará a extensão ao arquivo `.gitattributes`.

### Fluxo de trabalho normal

Depois de configurar o Git LFS, você pode usar os comandos Git normais. O Git LFS interceptará automaticamente os arquivos configurados:

```
git add .
git commit -m "Adiciona novos modelos 3D"
git push
```

## Limitações do GitHub

É importante observar que o GitHub tem algumas limitações para o Git LFS:

1. **Limite de armazenamento**: Repositórios gratuitos têm um limite de 1GB para armazenamento LFS e 1GB para largura de banda mensal.
2. **Limite de tamanho de arquivo**: Arquivos individuais não podem exceder 100MB no plano gratuito.

Para projetos maiores, considere:
- Atualizar para um plano pago do GitHub
- Usar o GitLab, que oferece 10GB de armazenamento LFS gratuito
- Usar uma solução de armazenamento separada para ativos muito grandes

## Boas práticas

1. **Seja seletivo**: Não adicione arquivos desnecessariamente grandes ao repositório.
2. **Compacte quando possível**: Reduza o tamanho de texturas e outros ativos antes de adicioná-los.
3. **Monitore o uso**: Fique atento ao tamanho do repositório para evitar atingir limites.
4. **Considere alternativas**: Para arquivos extremamente grandes, considere usar um sistema de gerenciamento de ativos separado.

## Solução de problemas

Se encontrar problemas com o Git LFS, tente:

```
git lfs fetch --all
git lfs pull
```

Para mais informações, consulte a [documentação oficial do Git LFS](https://git-lfs.github.com/).