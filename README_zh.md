# shiertier_scrapy

[English](https://github.com/shiertier-utils/shiertier_scrapy/blob/main/README.md) | 中文

## 简介

`shiertier_scrapy` 是一个 Python 库，旨在简化从网络下载图像的过程。它提供了一个强大且灵活的接口，用于处理各种 HTTP 状态码、重试和图像验证。该库特别适用于需要下载图像的网络爬虫任务。

## 安装

您可以通过 `pip` 安装 `shiertier_scrapy`：

```bash
pip install git+https://github.com/shiertier/shiertier_scrapy.git
```

请注意，该项目仍在开发中。

## 环境变量和存储位置

### 环境变量

- `SCRAPY_SAVE_DIR`: 下载图像的存储目录。如果未提供，将使用当前工作目录。

### 设置存储位置

您可以通过设置 `SCRAPY_SAVE_DIR` 环境变量来指定存储位置：

```bash
export SCRAPY_SAVE_DIR=/path/to/save_directory
```

或者，您可以在初始化 `ScrapyClientBase` 类时传递 `save_dir` 参数：

```python
from shiertier_scrapy import ScrapyClientBase

# 使用自定义存储目录初始化
scrapy_client = ScrapyClientBase(save_dir='/path/to/save_directory')
```

## 使用方法

### 下载单个图像

您可以使用 `download_one` 方法下载单个图像。该方法需要图像的 URL 和所需的保存名称。它还支持重试和重试之间的睡眠时间。

```python
from shiertier_scrapy import easy_scrapy_client

# 下载单个图像
easy_scrapy_client.download_one(url='http://example.com/image.jpg', save_name='image.jpg')
```

### 下载多个图像

您可以使用 `download_images` 方法并发下载多个图像。该方法需要一个 URL 列表和相应的保存名称列表。它还支持重试和重试之间的睡眠时间。

```python
from shiertier_scrapy import easy_scrapy_client

# URL 和保存名称
urls = ['http://example.com/image1.jpg', 'http://example.com/image2.jpg']
save_names = ['image1.jpg', 'image2.jpg']

# 下载多个图像
easy_scrapy_client.download_images(urls=urls, save_names=save_names)
```

## 依赖

- `requests`
- `Pillow`
- `shiertier_logger`
- `tqdm`

## 许可证

本项目基于 MIT 许可证发布。有关详细信息，请参阅 [LICENSE](LICENSE) 文件。