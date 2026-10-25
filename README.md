# Código-fonte da central de suporte PowerCloud

Este repositório publica o **código-fonte correspondente** da central de suporte da
PowerCloud (`suporte.powercloudconsultoria.com`). A central é uma versão modificada do
[Helpin](https://github.com/helpin-ai/helpin), software livre da Helpin AI.

A publicação atende à seção 13 da GNU Affero General Public License v3 (AGPL-3.0): quem
interage com a aplicação pela rede tem direito de receber o código-fonte da versão que
está em execução.

## Onde está o código

O código **não** fica na árvore deste repositório. Cada versão colocada em produção é
publicada como um **Release** (aba *Releases*), com:

- `helpin-powercloud-source-<commit>.tar.gz`: o conteúdo completo do commit implantado
  (`git archive`), incluindo as modificações da PowerCloud, os scripts de build e os
  arquivos de implantação, além de `PC-SOURCE-REVISION.txt` com o commit e a data;
- `helpin-powercloud-source-<commit>.tar.gz.sha256`: o hash SHA-256 do pacote.

A tag de cada Release identifica o commit (`pc-<12 primeiros caracteres do SHA>`). O link
"Código-fonte" no rodapé da central aponta para o Release da versão em produção.

O pacote nunca contém arquivos de ambiente (`.env`), credenciais nem configuração do
servidor de implantação. Antes de cada publicação o conteúdo é verificado por uma
varredura de segredos.

## Licença

- **Aplicação:** AGPL-3.0-only. O texto completo está em [`LICENSE`](LICENSE) (cópia
  de `LICENSE-AGPL-3.0` do código-fonte).
- **Widget e SDKs** (`widget/` e `packages/*`): Apache-2.0, com o arquivo `LICENSE` em
  cada diretório e o texto em `LICENSE-APACHE-2.0`.
- **Material de terceiros** (por exemplo `third_party/agent-runtime`): mantém as próprias
  licenças e arquivos `LICENSE`/`NOTICE`.
- Os avisos de copyright da **Helpin AI** e dos demais autores estão preservados no
  código-fonte. O arquivo `LICENSE` na raiz do pacote descreve o alcance de cada licença.
- Nenhum direito sobre o nome, o logotipo ou outras marcas **Helpin** é concedido por
  esta publicação.

## Como reconstruir

1. Baixe o `.tar.gz` do Release desejado e confira o hash:
   `shasum -a 256 -c helpin-powercloud-source-<commit>.tar.gz.sha256`
2. Extraia: `tar -xzf helpin-powercloud-source-<commit>.tar.gz`
3. Siga `deploy/dokploy/README.md` dentro do pacote: ele descreve a stack (Docker
   Compose), os requisitos de host, as variáveis de ambiente (modelo em
   `deploy/dokploy/.env.example`) e a ordem do primeiro deploy.
4. As modificações da PowerCloud em relação ao Helpin estão listadas em `POWERCLOUD.md`.

## Contato

Pedidos relacionados ao código-fonte: abra uma *issue* neste repositório.
