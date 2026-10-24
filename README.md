# Vietnamese SMS Spam Detection

Vietnamese SMS spam classification with PyTorch and the Hugging Face checkpoint `khanhthuan1995/autotrain-sms-spam-vietnamese-51799122495`.

## Results

All models were evaluated on the same stratified hold-out test split of 673 messages (568 Ham, 105 Spam), using seed 42. The best epoch was selected by validation Spam F1 before the test evaluation.

| Stage | Accuracy | Spam precision | Spam recall | Spam F1 | Macro F1 |
|---|---:|---:|---:|---:|---:|
| Baseline checkpoint | 84.40% | 50.00% | 0.95% | 1.87% | 46.70% |
| Head-only fine-tuning | 95.69% | 88.78% | 82.86% | 85.71% | 91.59% |
| Full-model fine-tuning | **96.88%** | **94.68%** | **84.76%** | **89.45%** | **93.81%** |

Final confusion matrix (rows: actual Ham/Spam; columns: predicted Ham/Spam):

```text
[[563,  5],
 [ 16, 89]]
```

See `results.csv` for the complete table. The public notebook is a sanitized source copy; recorded metrics were extracted from the executed notebook supplied with the project.

## Run

```bash
python -m pip install -r requirements.txt
python -m notebook "Vietnamese SMS Spam Detect.ipynb"
```

Place `vi_dataset.csv` beside the notebook before running. The dataset is not published because its supplied archive did not document redistribution provenance. The notebook performs cleaning and a stratified 70/15/15 split.

## Tóm tắt

Mô hình tốt nhất đạt **96,88% Accuracy** và **89,45% F1 lớp Spam** trên tập test giữ riêng gồm 673 tin nhắn. Quy trình lựa chọn mô hình sử dụng validation Spam F1 và chỉ đánh giá test sau khi chọn epoch.
