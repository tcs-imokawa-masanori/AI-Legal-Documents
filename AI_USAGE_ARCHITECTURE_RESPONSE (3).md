# 第21条（生成AIの使用）に関するご質問への回答
# Response to Questions Regarding Article 21 (Use of Generative AI)

**作成日 / Date**: 2026年1月13日 / January 13, 2026
**対象 / Subject**: 御社からのご質問（第21条関連） / Customer Inquiries (Article 21)

---

## ご質問への回答 / Responses to Your Questions

### 質問1 / Question 1: 機密情報が本件機能に保存されるリスクについて
### Risk of Confidential Information Being Stored in the AI System

**ご質問内容 / Your Question**:
> 「本件機能の学習データとして使用される」とありますが、我社が指定する機密情報が本件機能に保存されるリスクがあるのかを教示願います。

> The clause states that data may be "used as training data for this function." Please advise on the risk of our designated confidential information being stored in the AI system.

**回答 / Response**:

本調査で使用するAnthropic社のClaude API（商用プラン）には、以下のデータ保護措置が講じられております。

The Anthropic Claude API (commercial plan) used in this survey has the following data protection measures in place:

| 項目 / Item | 内容 / Details |
|-------------|----------------|
| **学習への使用 / Use for Training** | 商用製品（Claude for Work、Anthropic API等）の入力・出力データは、**デフォルトでモデルの学習には使用されません** / Input/output data from commercial products (Claude for Work, Anthropic API, etc.) is **NOT used for model training by default** |
| **データ保持期間 / Data Retention Period** | APIリクエストは最大30日間保持（2025年9月14日以降は7日間に短縮）、その後自動削除 / API requests are retained for up to 30 days (reduced to 7 days after September 14, 2025), then automatically deleted |
| **長期保存 / Long-term Storage** | 保持期間経過後、入力データは完全削除され、永続的に保存されることはありません / After the retention period, input data is completely deleted and never permanently stored |
| **モデルへの影響 / Impact on Model** | 入力された情報がAIモデル自体に「記憶」または「組み込まれる」ことはありません / Input information is NOT "memorized" or "incorporated" into the AI model itself |

**リスク評価 / Risk Assessment**:
- **短期的リスク（7-30日以内）/ Short-term Risk (within 7-30 days)**: 限定的 - 不正利用監視目的での一時保持のみ / Limited - temporary retention for abuse monitoring only
- **長期的リスク（保持期間経過後）/ Long-term Risk (after retention period)**: なし - データは完全削除 / None - data is completely deleted

---

### 質問2 / Question 2: 提供元第三者以外の組織による機密情報へのアクセスリスクについて
### Risk of Third-Party Access to Confidential Information

**ご質問内容 / Your Question**:
> 「本件機能の学習データとして使用される」とありますが、提供元第三者以外の組織が我社が指定する機密情報にアクセスするリスクがあるのかを教示願います。

> Please advise on the risk of organizations other than the provider accessing our designated confidential information.

**回答 / Response**:

| アクセス主体 / Access Entity | アクセス可能性 / Access Possibility | 備考 / Notes |
|------------------------------|-------------------------------------|--------------|
| **Anthropic社 / Anthropic** | 限定的に可能 / Limited access possible | 安全性・不正利用監視目的のみ。厳格なアクセス制御下で必要最小限の担当者のみ / For safety and abuse monitoring only. Strictly controlled, minimum necessary personnel |
| **Anthropic社以外の第三者 / Third parties other than Anthropic** | なし / None | APIデータは第三者への提供・販売は行われません / API data is not shared with or sold to third parties |
| **他のAPIユーザー / Other API users** | なし / None | ユーザー間でのデータ共有は一切ありません / No data sharing between users |
| **政府機関 / Government agencies** | 法的義務による場合のみ / Only under legal obligation | 法令に基づく開示要求がある場合に限定 / Limited to legally mandated disclosure requests |

**セキュリティ対策 / Security Measures**:
- すべての通信はTLS暗号化（HTTPS） / All communications are TLS encrypted (HTTPS)
- データは転送時・保存時ともに暗号化 / Data is encrypted in transit and at rest
- SOC 2 Type II認証取得済み / SOC 2 Type II certified
- ISO 27001、ISO 42001認証取得済み / ISO 27001 and ISO 42001 certified
- アクセスログの厳格な管理 / Strict access log management

---

### 質問3 / Question 3: 調査環境の俯瞰図（アーキテクチャ図）
### Survey Environment Overview (Architecture Diagram)

以下に、本調査で想定する環境のアーキテクチャ図を提示いたします。

Below is the architecture diagram for the survey environment.

---

## 主要AIプラットフォームのデータ取扱い比較
## Comparison of Data Handling Across Major AI Platforms

### データ取扱いポリシー比較表 / Data Handling Policy Comparison

| プロバイダー / Provider | 学習への使用 / Used for Training | データ保持期間 / Retention Period | 第三者共有 / Third-Party Sharing | ZDR対応 / ZDR Support |
|------------------------|----------------------------------|----------------------------------|----------------------------------|----------------------|
| **Anthropic Claude API** | × 使用しない / Not used | 7-30日 / 7-30 days | × なし / None | ○ 可能 / Available |
| **AWS Bedrock** | × 使用しない / Not used | 保存なし / No storage | × なし / None | ○ デフォルト / Default |
| **Azure OpenAI** | × 使用しない / Not used | 最大30日 / Up to 30 days | × なし / None | ○ 申請制 / By request |
| **OpenAI API** | × 使用しない / Not used | 最大30日 / Up to 30 days | × なし / None | ○ 申請制 / By request |
| **Google Vertex AI** | × 使用しない / Not used | 24時間(メモリ) / 24h (in-memory) | × なし / None | ○ 申請制 / By request |

※ ZDR = Zero Data Retention（ゼロデータ保持）/ Zero Data Retention

---

## 各プラットフォームの詳細 / Platform Details

### 1. Anthropic Claude API / Claude for Work

**公式ポリシー / Official Policy（[Anthropic Privacy Center](https://privacy.claude.com/en/articles/10023580-is-my-data-used-for-model-training)より / from）**:

> "By default, we will not use your inputs or outputs from our commercial products (e.g. Claude for Work, Anthropic API, Claude Gov, etc.) to train our models."

| 項目 / Item | 内容 / Details |
|-------------|----------------|
| **適用規約 / Applicable Terms** | Commercial Terms（商用利用規約） |
| **学習への使用 / Use for Training** | × デフォルトで使用しない / Not used by default |
| **データ保持 / Data Retention** | API: 7日間（2025年9月14日以降）/ 30日間（それ以前） / 7 days (after Sep 14, 2025) / 30 days (before) |
| **ZDR（ゼロ保持）/ ZDR** | DPA（データ処理契約）により設定可能 / Configurable via DPA |
| **第三者アクセス / Third-Party Access** | × なし（AWS Bedrock/Google Vertex AI経由も同様）/ None (same via AWS Bedrock/Google Vertex AI) |

**セキュリティ認証 / Security Certifications**:

| 認証 / Certification | Claude API | Claude Enterprise | Claude on Bedrock | Claude on Vertex AI |
|---------------------|:----------:|:-----------------:|:-----------------:|:-------------------:|
| SOC 2 Type II | ✓ | ✓ | ✓ | ✓ |
| ISO 27001 | ✓ | ✓ | ✓ | ✓ |
| ISO 42001 | ✓ | ✓ | ✓ | ✓ |
| CSA Star | ✓ | ✓ | ✓ | ✓ |
| HIPAA | ✓ | ✓ | N/A | N/A |

**参照 / Reference**: [Trust Center - Anthropic](https://www.anthropic.com/trust-center)

---

### 2. AWS Amazon Bedrock

**公式ポリシー / Official Policy（[AWS Bedrock Security](https://aws.amazon.com/bedrock/security-compliance/)より / from）**:

> "Amazon Bedrock doesn't store or log your prompts and completions. Amazon Bedrock doesn't use your prompts and completions to train any AWS models and doesn't distribute them to third parties."

| 項目 / Item | 内容 / Details |
|-------------|----------------|
| **学習への使用 / Use for Training** | × 使用しない / Not used |
| **データ保存 / Data Storage** | × 保存しない（デフォルト）/ Not stored (default) |
| **モデルプロバイダーアクセス / Model Provider Access** | × なし（専用アカウントで隔離）/ None (isolated in dedicated account) |
| **カスタムモデル / Custom Models** | お客様データで作成した場合も元のFMには影響なし / Customer data used for custom models does not affect original FM |
| **暗号化 / Encryption** | AES-256（保存時）、TLS（転送時）、KMS対応 / AES-256 (at rest), TLS (in transit), KMS supported |

**特徴 / Features**:
- モデルプロバイダー（Anthropic等）はAWSのBedrock環境にアクセス不可 / Model providers (Anthropic, etc.) cannot access AWS Bedrock environment
- 完全に隔離された専用デプロイメントアカウント / Completely isolated dedicated deployment account
- お客様のVPC内でデータ転送 / Data transfer within customer's VPC

**参照 / Reference**: [Amazon Bedrock Data Protection](https://docs.aws.amazon.com/bedrock/latest/userguide/data-protection.html)

---

### 3. Azure OpenAI Service

**公式ポリシー / Official Policy（[Microsoft Learn](https://learn.microsoft.com/en-us/legal/cognitive-services/openai/data-privacy)より / from）**:

> "Customer Data, Prompts, and Completions are NOT used to improve Microsoft or third-party products or services without your explicit permission or instruction."

| 項目 / Item | 内容 / Details |
|-------------|----------------|
| **学習への使用 / Use for Training** | × 使用しない / Not used |
| **データ保持 / Data Retention** | 最大30日間（不正利用監視目的）/ Up to 30 days (for abuse monitoring) |
| **ZDR対応 / ZDR Support** | EA/MCA契約で申請可能 / Available with EA/MCA agreement |
| **OpenAIとの分離 / Separation from OpenAI** | 完全分離（OpenAI社のサービスとは非連携）/ Completely separated (not connected to OpenAI services) |
| **データ所在地 / Data Location** | 選択したAzureリージョン内 / Within selected Azure region |

**重要事項 / Important Notes**:
- Microsoft Azure環境内でホスト / Hosted within Microsoft Azure environment
- OpenAI社（ChatGPT等）とは完全に分離 / Completely separated from OpenAI (ChatGPT, etc.)
- Fine-tuning時の一時的なデータ移動あり（2025年3月更新）/ Temporary data relocation during fine-tuning (March 2025 update)

**参照 / Reference**: [Azure OpenAI Data Privacy](https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/openai/data-privacy)

---

### 4. OpenAI API (Direct)

**公式ポリシー / Official Policy（[OpenAI Enterprise Privacy](https://openai.com/enterprise-privacy/)より / from）**:

> "As of March 1, 2023, data sent to the OpenAI API is not used to train or improve OpenAI models (unless you explicitly opt in)."

| 項目 / Item | 内容 / Details |
|-------------|----------------|
| **学習への使用 / Use for Training** | × デフォルトで使用しない（オプトイン制）/ Not used by default (opt-in) |
| **データ保持 / Data Retention** | 最大30日間（不正利用監視目的）/ Up to 30 days (for abuse monitoring) |
| **ZDR対応 / ZDR Support** | 申請により設定可能 / Configurable by request |
| **暗号化 / Encryption** | AES-256（保存時）、TLS 1.2+（転送時）/ AES-256 (at rest), TLS 1.2+ (in transit) |
| **データ所在地 / Data Location** | 米国、欧州、日本等選択可能 / US, Europe, Japan, etc. selectable |

**Enterprise Key Management (EKM)**:
- お客様管理の暗号化キーに対応 / Supports customer-managed encryption keys
- より高いセキュリティ・コンプライアンス要件に対応 / Meets higher security and compliance requirements

**参照 / Reference**: [OpenAI Data Controls](https://platform.openai.com/docs/guides/your-data)

---

### 5. Google Cloud Vertex AI

**公式ポリシー / Official Policy（[Google Cloud](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/vertex-ai-zero-data-retention)より / from）**:

> "By default, Google Cloud doesn't use customer data to train its foundation models; this includes prompts, responses, and any adapter model training data."

| 項目 / Item | 内容 / Details |
|-------------|----------------|
| **学習への使用 / Use for Training** | × 使用しない / Not used |
| **データ保持 / Data Retention** | 24時間（インメモリキャッシュ、レイテンシ削減目的）/ 24 hours (in-memory cache for latency reduction) |
| **ZDR対応 / ZDR Support** | 申請により例外設定可能 / Exemption configurable by request |
| **暗号化 / Encryption** | 転送時・保存時ともに暗号化 / Encrypted in transit and at rest |
| **データ所在地 / Data Location** | リージョン/マルチリージョンAPIで選択可能 / Selectable via regional/multi-regional API |

**特徴 / Features**:
- プロジェクトレベルでの隔離 / Project-level isolation
- Geminiモデル使用時もデータは学習に使用されない / Data not used for training even with Gemini models

**参照 / Reference**: [Vertex AI Security Controls](https://docs.cloud.google.com/vertex-ai/docs/general/vertexai-security-controls)

---

## 調査環境アーキテクチャ図 / Survey Environment Architecture Diagram

### 全体構成図 / Overall Configuration Diagram

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                        御社環境 / Customer Environment                        │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────────┐    ┌─────────────────────┐                         │
│  │    調査担当者        │    │   機密情報管理者     │                         │
│  │  TCS Consultant     │    │  Customer Admin     │                         │
│  └──────────┬──────────┘    └──────────┬──────────┘                         │
│             │                          │                                     │
│             │ ①調査票入力               │ ②機密レベル判定                     │
│             │ Survey Input             │ Confidentiality Assessment         │
│             ▼                          ▼                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                   調査プラットフォーム / Survey Platform              │    │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────────┐  │    │
│  │  │ 入力フォーム   │  │ 機密情報      │  │ 匿名化・マスキング処理    │  │    │
│  │  │ Input Form   │  │ フィルター    │  │ Anonymization &         │  │    │
│  │  │              │  │ Confidential │  │ Masking Process         │  │    │
│  │  │              │  │ Filter       │  │                          │  │    │
│  │  └──────┬───────┘  └──────┬───────┘  └───────────┬──────────────┘  │    │
│  │         │                 │                      │                 │    │
│  │         └─────────────────┴──────────────────────┘                 │    │
│  │                           │                                        │    │
│  └───────────────────────────┼────────────────────────────────────────┘    │
│                              │                                             │
└──────────────────────────────┼─────────────────────────────────────────────┘
                               │
                               │ ③匿名化済みデータのみ送信
                               │ Only anonymized data transmitted
                               │ (TLS暗号化通信 / TLS Encrypted)
                               ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                        インターネット / Internet (HTTPS/TLS 1.2+)             │
└──────────────────────────────┬───────────────────────────────────────────────┘
                               │
          ┌────────────────────┼────────────────────┐
          │                    │                    │
          ▼                    ▼                    ▼
┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
│ Option A        │  │ Option B        │  │ Option C        │
│ Anthropic       │  │ AWS Bedrock     │  │ Azure OpenAI    │
│ Claude API      │  │ (Claude)        │  │                 │
└────────┬────────┘  └────────┬────────┘  └────────┬────────┘
         │                    │                    │
         ▼                    ▼                    ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│              各プラットフォームの共通保証 / Common Guarantees                  │
├──────────────────────────────────────────────────────────────────────────────┤
│  ┌────────────────────────────────────────────────────────────────────────┐  │
│  │  ✓ 入力データをモデルの学習には使用しない                               │  │
│  │    Input data is NOT used for model training                          │  │
│  │  ✓ 第三者への顧客データ共有なし                                         │  │
│  │    NO sharing of customer data with third parties                     │  │
│  │  ✓ 一時保持後の自動削除（7-30日）                                       │  │
│  │    Automatic deletion after temporary retention (7-30 days)           │  │
│  │  ✓ 転送時・保存時の暗号化                                               │  │
│  │    Encryption in transit and at rest                                  │  │
│  │  ✓ SOC 2 Type II等のセキュリティ認証取得                                │  │
│  │    Security certifications (SOC 2 Type II, etc.)                      │  │
│  └────────────────────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────────────────────┘

                    ═══════════════════════════════════════
                     × 学習データとしての使用なし
                       NOT used as training data
                     × 第三者へのデータ共有なし
                       NO third-party data sharing
                     × 永続的なデータ保存なし
                       NO permanent data storage
                    ═══════════════════════════════════════
```

---

### マルチクラウド対応アーキテクチャ / Multi-Cloud Architecture

```
                    ┌─────────────────────────────────────┐
                    │       御社データセンター              │
                    │    Customer Data Center             │
                    └─────────────────┬───────────────────┘
                                      │
                    ┌─────────────────┼───────────────────┐
                    │                 │                   │
          ┌─────────▼─────────┐       │       ┌───────────▼─────────┐
          │  AWS環境          │       │       │  Azure環境          │
          │  AWS Environment  │       │       │  Azure Environment  │
          │  ┌─────────────┐  │       │       │  ┌─────────────┐    │
          │  │ Amazon      │  │       │       │  │ Azure       │    │
          │  │ Bedrock     │  │       │       │  │ OpenAI      │    │
          │  │ ┌─────────┐ │  │       │       │  │ Service     │    │
          │  │ │ Claude  │ │  │       │       │  │ ┌─────────┐ │    │
          │  │ │ Sonnet  │ │  │       │       │  │ │ GPT-4   │ │    │
          │  │ └─────────┘ │  │       │       │  │ └─────────┘ │    │
          │  └─────────────┘  │       │       │  └─────────────┘    │
          │                   │       │       │                     │
          │  データ保存なし   │       │       │  30日後自動削除     │
          │  No data storage  │       │       │  Auto-delete: 30d   │
          │  学習使用なし     │       │       │  No training use    │
          │  No training use  │       │       │                     │
          └───────────────────┘       │       └─────────────────────┘
                                      │
                    ┌─────────────────▼───────────────────┐
                    │       Google Cloud環境              │
                    │    Google Cloud Environment        │
                    │  ┌─────────────────────────────┐    │
                    │  │ Vertex AI                   │    │
                    │  │ ┌─────────┐  ┌─────────┐   │    │
                    │  │ │ Gemini  │  │ Claude  │   │    │
                    │  │ └─────────┘  └─────────┘   │    │
                    │  └─────────────────────────────┘    │
                    │                                     │
                    │  24時間インメモリのみ               │
                    │  24h in-memory only                │
                    │  学習使用なし / No training use     │
                    └─────────────────────────────────────┘

  ╔════════════════════════════════════════════════════════════════════════╗
  ║  全プラットフォーム共通: 顧客データはモデル学習に使用されません          ║
  ║  Common to all platforms: Customer data is NOT used for model training ║
  ╚════════════════════════════════════════════════════════════════════════╝
```

---

### データフロー詳細図 / Data Flow Detail Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    データフロー概要 / Data Flow Overview                     │
└─────────────────────────────────────────────────────────────────────────────┘

  ┌──────────┐      ┌──────────┐      ┌──────────┐      ┌──────────┐
  │ 入力データ │  →   │ 機密判定  │  →   │ 匿名化   │  →   │ API送信  │
  │ Input    │      │ Classify │      │Anonymize │      │ API Send │
  └──────────┘      └──────────┘      └──────────┘      └──────────┘
        │                 │                 │                 │
        ▼                 ▼                 ▼                 ▼
  ┌──────────┐      ┌──────────┐      ┌──────────┐      ┌──────────┐
  │調査票回答 │      │機密レベル │      │ 個人情報  │      │TLS暗号化 │
  │Survey    │      │ 高:除外   │      │ マスキング│      │ TLS      │
  │Response  │      │ High:Excl│      │ PII Mask │      │ Encrypt  │
  │インタビュー│      │ 中:匿名化 │      │ 固有名詞  │      │  送信    │
  │Interview │      │ Med:Anon │      │ Replace  │      │  Send    │
  │ 議事録   │      │ 低:通過   │      │ Names    │      │          │
  │ Minutes  │      │ Low:Pass │      │          │      │          │
  └──────────┘      └──────────┘      └──────────┘      └──────────┘


  ═══════════════════════════════════════════════════════════════════════
              機密情報保護の多層防御 / Multi-Layer Defense
  ═══════════════════════════════════════════════════════════════════════

  Layer 1: 入力段階での制御 / Input Stage Control
  ├── 機密レベル「高」の情報は入力を禁止
  │   High-confidentiality information is prohibited from input
  └── 業務ルールによる入力ガイドライン
      Input guidelines based on business rules

  Layer 2: 送信前の匿名化処理 / Pre-transmission Anonymization
  ├── 個人情報（氏名、メールアドレス等）のマスキング
  │   Masking of PII (names, email addresses, etc.)
  ├── 会社固有情報の一般化
  │   Generalization of company-specific information
  └── システム名・プロジェクト名の置換
      Replacement of system/project names

  Layer 3: 通信の暗号化 / Communication Encryption
  ├── TLS 1.2以上での暗号化通信
  │   Encrypted communication via TLS 1.2+
  └── API認証キーによるアクセス制御
      Access control via API authentication keys

  Layer 4: プラットフォーム側の保護措置 / Platform-side Protections
  ├── 一定期間後の自動データ削除
  │   Automatic data deletion after specified period
  ├── 学習データとしての使用禁止（全プラットフォーム共通）
  │   Prohibition of use as training data (common to all platforms)
  └── 第三者へのデータ非開示
      Non-disclosure of data to third parties
```

---

### セキュリティ境界と責任分界 / Security Boundaries and Responsibility Matrix

```
┌─────────────────────────────────────────────────────────────────────────────┐
│           責任分界点 / Responsibility Matrix (RACI)                         │
└─────────────────────────────────────────────────────────────────────────────┘

                    御社責任              TCS責任           AI Provider責任
                    Customer          Consultant      (Anthropic/AWS/Azure/
                                                       OpenAI/Google)
                      │                    │                    │
  ┌───────────────────┼────────────────────┼────────────────────┼──────────┐
  │ 機密情報の分類・   │◀══════════════════│                    │          │
  │ レベル判定         │                    │                    │          │
  │ Confidentiality   │                    │                    │          │
  │ Classification    │                    │                    │          │
  ├───────────────────┼────────────────────┼────────────────────┼──────────┤
  │ 入力データの       │                    │◀══════════════════│          │
  │ 匿名化・マスキング │                    │                    │          │
  │ Data Anonymization│                    │                    │          │
  │ & Masking         │                    │                    │          │
  ├───────────────────┼────────────────────┼────────────────────┼──────────┤
  │ 調査実施・         │                    │◀══════════════════│          │
  │ 分析レポート作成   │                    │                    │          │
  │ Survey & Report   │                    │                    │          │
  ├───────────────────┼────────────────────┼────────────────────┼──────────┤
  │ API基盤の          │                    │                    │◀════════│
  │ セキュリティ       │                    │                    │          │
  │ API Security      │                    │                    │          │
  ├───────────────────┼────────────────────┼────────────────────┼──────────┤
  │ データの一時保管   │                    │                    │◀════════│
  │ および削除         │                    │                    │          │
  │ Data Retention    │                    │                    │          │
  │ & Deletion        │                    │                    │          │
  ├───────────────────┼────────────────────┼────────────────────┼──────────┤
  │ 学習への非使用     │                    │                    │◀════════│
  │ の保証             │                    │                    │          │
  │ Non-training      │                    │                    │          │
  │ Guarantee         │                    │                    │          │
  └───────────────────┴────────────────────┴────────────────────┴──────────┘
```

---

## 運用上の保護措置 / Operational Safeguards

### 弊社（TCS）が実施する保護措置 / Safeguards Implemented by TCS

| # | 保護措置 / Safeguard | 内容 / Details |
|---|----------------------|----------------|
| 1 | **機密情報入力ガイドライン / Confidential Information Input Guidelines** | 機密レベル「高」の情報はAIへの入力を禁止 / High-confidentiality information is prohibited from AI input |
| 2 | **匿名化処理 / Anonymization Processing** | 個人名、会社固有システム名等を送信前にマスキング / Masking personal names, company-specific system names before transmission |
| 3 | **入力レビュー / Input Review** | 機密情報が含まれていないことを送信前に確認 / Confirm no confidential information before sending |
| 4 | **アクセス管理 / Access Management** | API利用者を限定し、利用ログを記録 / Limit API users and record usage logs |
| 5 | **データ最小化 / Data Minimization** | 分析に必要最小限の情報のみを入力 / Input only minimum necessary information for analysis |
| 6 | **プラットフォーム選定 / Platform Selection** | セキュリティ要件に応じた適切なプラットフォーム選定 / Select appropriate platform based on security requirements |

### 御社にご確認いただきたい事項 / Items to Confirm with Customer

| # | 確認事項 / Item | 目的 / Purpose |
|---|-----------------|----------------|
| 1 | 機密情報の分類基準 / Confidentiality classification criteria | 入力可否判断の基準明確化 / Clarify criteria for input decisions |
| 2 | 入力禁止情報リスト / List of prohibited information | 絶対に入力してはいけない情報の特定 / Identify information that must never be input |
| 3 | 匿名化ルール / Anonymization rules | 固有名詞等の置換ルール合意 / Agree on replacement rules for proper nouns |
| 4 | 使用プラットフォーム / Platform preference | ご希望のクラウドプラットフォーム / Preferred cloud platform |

---

## まとめ / Summary

| 質問 / Question | 回答要約 / Response Summary |
|-----------------|----------------------------|
| **1. データ保存リスク / Data Storage Risk** | 全プラットフォームにおいて、APIデータはモデルの学習には使用されません。一時保持（7-30日）後、完全削除。永続保存なし。 / Across all platforms, API data is NOT used for model training. Complete deletion after temporary retention (7-30 days). No permanent storage. |
| **2. 第三者アクセスリスク / Third-Party Access Risk** | 全プラットフォームにおいて、第三者へのデータ共有は行われません。各プロバイダー内でも厳格なアクセス制御。 / Across all platforms, NO data sharing with third parties. Strict access control even within each provider. |
| **3. 環境俯瞰図 / Environment Overview** | 上記アーキテクチャ図の通り、複数プラットフォーム対応可能。多層防御と責任分界を明確化。 / As shown in the architecture diagrams above, multiple platforms are supported. Multi-layer defense and clear responsibility boundaries. |

---

## 参考情報・出典 / References and Sources

### Anthropic Claude
- [Is my data used for model training? | Anthropic Privacy Center](https://privacy.claude.com/en/articles/10023580-is-my-data-used-for-model-training)
- [Data usage - Claude Code Docs](https://docs.anthropic.com/en/docs/build-with-claude/claude-code/overview#data-handling)
- [Trust Center - Anthropic](https://www.anthropic.com/trust-center)

### AWS Amazon Bedrock
- [Data protection - Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/data-protection.html)
- [Amazon Bedrock Security and Privacy](https://aws.amazon.com/bedrock/security-compliance/)
- [Amazon Bedrock FAQs](https://aws.amazon.com/bedrock/faqs/)

### Azure OpenAI
- [Data, privacy, and security for Azure OpenAI Service](https://learn.microsoft.com/en-us/legal/cognitive-services/openai/data-privacy)
- [Azure OpenAI Data Retention Privacy 2025](https://learn.microsoft.com/en-us/answers/questions/2181252/azure-openai-data-retention-privacy-2025)

### OpenAI API
- [Enterprise privacy at OpenAI](https://openai.com/enterprise-privacy/)
- [Data controls in the OpenAI platform](https://platform.openai.com/docs/guides/your-data)
- [How your data is used to improve model performance](https://openai.com/policies/how-your-data-is-used-to-improve-model-performance/)

### Google Cloud Vertex AI
- [Vertex AI and zero data retention](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/vertex-ai-zero-data-retention)
- [Security controls for Vertex AI](https://docs.cloud.google.com/vertex-ai/docs/general/vertexai-security-controls)
- [Data governance and generative AI](https://docs.cloud.google.com/generative-ai-app-builder/docs/data-governance)

---

**本資料に関するお問い合わせ / Contact for this document**:
TCS EA推進チーム / TCS EA Promotion Team

*作成日 / Created: 2026年1月13日 / January 13, 2026*
