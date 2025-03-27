---
title: 'CVAT Overview'
linkTitle: 'Introduction to CVAT'
weight: 1
description: 'The open-source tool for image and video annotation'
---

CVAT (Computer Vision Annotation Tool) is open-source software designed for annotating images and videos used in machine learning (ML) tasks. It is widely used for object detection, image segmentation, pose estimation, and other AI/ML applications. With CVAT, you can improve the data quality and prepare it for your ML models.

CVAT is originally developed by Intel and maintained by [CVAT.ai](https://www.cvat.ai/).

CVAT is available in two versions:

- [**Online version**](https://app.cvat.ai/) is web-based application that runs on CVAT.ai servers.
  All you need is a modern browser and stable internet connection. CVAT Online has [free and paid plans](https://www.cvat.ai/pricing/cvat-online) and is better suited for individuals and small teams that do not need strict privacy needs, custom workflows or large-scale integration.
  To learn which plan suits your needs the best, refer to [**our blog article**](https://www.cvat.ai/post/cvat-ai-pricing-plans-choosing-the-right-plan-for-your-needs).

- **Self-hosted version** allows you to run CVAT on your own servers or cloud infrastructure. This version is ideal for teams and organizations that need full control over data, security, and performance. CVAT Self-hosted version comes as two editions:
    - **Community edition** is **free** open-sourced edition that provides the main CVAT functionality with limited advanced features.
    - **Enterprise edition** is paid edition with **Enterprise-level support**,
    and full advanced features such as **SSO**, **LDAP**, integrations with
    [**Roboflow and HuggingFace**](https://www.cvat.ai/post/integrating-hugging-face-and-roboflow-models),
    and **advanced analytics**. CVAT.ai also offers **professional training** and **24-hour SLA support** for Enterprise edition users.
    To learn more about **Enterprise edition** features, refer to [**Paid features**](/docs/enterprise/).

    You can compare the plans and available features for CVAT Community and Enterprise editions on [**CVAT.ai**](https://www.cvat.ai/pricing/cvat-on-prem).

## Key features

### Data formats

CVAT supports the following data formats:

- **3D**: `.pcd`, `.bin`
- **Image**: everything supported by the Python
  [**Pillow library**](https://pillow.readthedocs.io/en/stable/handbook/image-file-formats.html),
  including formats like `.jpeg`, `.png`, `.bmp`, `.gif`, `.ppm`and `.tiff`
- **Video**: all formats, supported by [FFmpeg](https://ffmpeg.org/), including `.mp4`, `.avi`, and `.mov`

To learn about annotation export and import formats, refer to
{{< ilink "/docs/manual/advanced/formats" "**Export annotations and data from CVAT**" >}}.

### Annotation tools

CVAT provides different tools for labeling images and videos, each designed for specific tasks:

<!--lint disable maximum-line-length-->

| Annotation Tool                                                                                          | Use Cases                                                                                                            |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| {{< ilink "/docs/manual/advanced/3d-object-annotation-advanced" "**3D Object Annotation**" >}}           | Ideal for projects that require depth perception and volume estimation, for example, autonomous vehicle training     |
| {{< ilink "/docs/manual/advanced/attribute-annotation-mode-advanced" "**Attribute Annotation Mode**" >}} | Useful for adding detailed information to objects, such as color, size, or other specific characteristics            |
| {{< ilink "/docs/manual/advanced/annotation-with-rectangles" "**Annotation with Rectangles**" >}}        | Best for simple object detection where objects have a box-like shape, such as windows in a building                  |
| {{< ilink "/docs/manual/advanced/annotation-with-polygons" "**Annotation with Polygons**" >}}            | Suited for complex shapes in images, for example, outlining geographical features on maps or detailed product shapes |
| {{< ilink "/docs/manual/advanced/annotation-with-polylines" "**Annotation with Polylines**" >}}          | Great for annotating linear objects (roads, pathways, or limbs in pose estimation)                                   |
| {{< ilink "/docs/manual/advanced/annotation-with-ellipses" "**Annotation with Ellipses**" >}}            | Ideal for such objects as plates, balls, or eyes, where a circular or oval annotation is needed                      |
| {{< ilink "/docs/manual/advanced/annotation-with-cuboids" "**Annotation with Cuboids**" >}}              | Useful for 3D objects in 2D images, for example, boxes or furniture in room layouts                                  |
| {{< ilink "/docs/manual/advanced/skeletons" "**Annotation with Skeletons**" >}}                          | Ideal for human pose estimation, animation, and movement analysis in sports or medical fields                        |
| {{< ilink "/docs/manual/advanced/annotation-with-brush-tool" "**Annotation with Brush Tool**" >}}        | Perfect for intricate and detailed annotations where precision is key, for example, in medical imaging               |
| {{< ilink "/docs/manual/advanced/annotation-with-tags" "**Annotation with Tags**" >}}                    | Useful for image and video classification tasks, such as identifying scenes or themes in a dataset                   |
<!--lint enable maximum-line-length-->

### Labeling algorithms

CVAT has automated labeling features that significantly enhance the annotation process and potentially speed it up to 10 times.

> **Note:**
> To learn more about annotation tools,
> refer to {{< ilink "/docs/manual/advanced/ai-tools" "**OpenCV and AI Tools**" >}}

CVAT supports the following labeling algorithms:

<!--lint disable maximum-line-length-->
<!-- The links in the table are not informative. I think it is better to provide a high-level overview for the algorithms. -->
| Algorithm                                                                                                                                           | Category   | Framework  | CPU Support | GPU Support |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ----------- | ----------- |
| [SegmentAnything](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/facebookresearch/sam/nuclio)                                     | Interactor | PyTorch    | ✔️          | ✔️          |
| [Deep Extreme Cut](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/dextr/nuclio)                                                   | Interactor | OpenVINO   | ✔️          |             |
| [Faster RCNN](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/public/faster_rcnn_inception_resnet_v2_atrous_coco/nuclio)       | Detector   | OpenVINO   | ✔️          |             |
| [Mask RCNN](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/public/mask_rcnn_inception_resnet_v2_atrous_coco/nuclio)           | Detector   | OpenVINO   | ✔️          |             |
| [YOLO v3](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/public/yolo-v3-tf/nuclio)                                            | Detector   | OpenVINO   | ✔️          |             |
| [YOLO v7](https://github.com/cvat-ai/cvat/tree/develop/serverless/onnx/WongKinYiu/yolov7/nuclio)                                                    | Detector   | ONNX       | ✔️          | ✔️          |
| [Object Reidentification](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/intel/person-reidentification-retail-0277/nuclio)    | ReID       | OpenVINO   | ✔️          |             |
| [Semantic Segmentation for ADAS](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/intel/semantic-segmentation-adas-0001/nuclio) | Detector   | OpenVINO   | ✔️          |             |
| [Text Detection v4](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/intel/text-detection-0004/nuclio)                          | Detector   | OpenVINO   | ✔️          |             |
| [SiamMask](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/foolwood/siammask/nuclio)                                                | Tracker    | PyTorch    | ✔️          | ✔️          |
| [TransT](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/dschoerk/transt/nuclio)                                                    | Tracker    | PyTorch    | ✔️          | ✔️          |
| [f-BRS](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/saic-vul/fbrs/nuclio)                                                       | Interactor | PyTorch    | ✔️          |             |
| [HRNet](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/saic-vul/hrnet/nuclio)                                                      | Interactor | PyTorch    |             | ✔️          |
| [Inside-Outside Guidance](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/shiyinzhang/iog/nuclio)                                   | Interactor | PyTorch    | ✔️          |             |
| [Faster RCNN](https://github.com/cvat-ai/cvat/tree/develop/serverless/tensorflow/faster_rcnn_inception_v2_coco/nuclio)                              | Detector   | TensorFlow | ✔️          | ✔️          |
| [RetinaNet](https://github.com/cvat-ai/cvat/tree/develop/serverless/pytorch/facebookresearch/detectron2/retinanet_r101/nuclio)                      | Detector   | PyTorch    | ✔️          | ✔️          |
| [Face Detection](https://github.com/cvat-ai/cvat/tree/develop/serverless/openvino/omz/intel/face-detection-0205/nuclio)                             | Detector   | OpenVINO   | ✔️          |             |

<!--lint enable maximum-line-length-->

### Integrations

CVAT integrates with some popular solutions:

<!--lint disable maximum-line-length-->

| Integrated Service                                                                  | CVAT version          | Description                                                                                                                                                                                                                                           |
| ----------------------------------------------------------------------------------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [**Human Protocol**](https://hmt.ai)                                                | CVAT Online and CVAT Self-hosted | Incorporates CVAT to augment annotation services within the Human Protocol framework, enhancing its capabilities in data labeling                                                                                                                    |
| [**FiftyOne**](https://fiftyone.ai)                                                 | CVAT Online and CVAT Self-hosted | An open-source tool for dataset management and model analysis in computer vision, FiftyOne is [closely integrated](https://voxel51.com/docs/fiftyone/integrations/cvat.html) with CVAT to enhance annotation capabilities and label refinement       |
| [**Hugging Face**](https://huggingface.co/) & [**Roboflow**](https://roboflow.com/) | CVAT Online                 | In CVAT Online, models from Hugging Face and Roboflow can be added to enhance computer vision tasks. For more information, refer to [**Integration with Hugging Face and Roboflow**](https://www.cvat.ai/post/integrating-hugging-face-and-roboflow-models) |

<!--lint enable maximum-line-length-->

> **Note:** If you're using CVAT, we'd love to
> hear from you at [contact@cvat.ai](mailto:contact+github@cvat.ai).

## Further reading

This section provides documentation links for further learning about CVAT.

<!--lint disable maximum-line-length-->

### CVAT Online

| Name                                                                                                    | Description                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| {{< ilink "/docs/manual" "**User Manual**" >}}                                                          | This comprehensive guide covers all CVAT tools available for work. It includes descriptions of all available tools, quality control methods, and procedures for importing and exporting data. This manual is relevant for both CVAT Online and Self-Hosted versions |
| {{< ilink "/docs/getting_started/workflow-org" "**CVAT Complete Workflow Guide for Organizations**" >}} | This guide provides a comprehensive overview of using CVAT for collaboration in organizations                                                                                                                                                                      |
| {{< ilink "/docs/enterprise/subscription-management" "**Subscription Management**" >}}                  | Learn how to [**choose a plan**](https://www.cvat.ai/post/cvat-ai-pricing-plans-choosing-the-right-plan-for-your-needs), subscribe, and manage your subscription effectively                                                                                       |
| {{< ilink "/docs/manual/advanced/xml_format" "**XML Annotation Format**" >}}                            | Detailed documentation on the XML format used for annotations in CVAT essential for understanding data structure and compatibility                                                                                                                                 |

### CVAT Self-Hosted

| Name                                                                                           | Description                                                                                                                                                                                                               |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| {{< ilink "/docs/administration/basics/installation" "**Self-hosted Installation Guide**" >}}  | Start here to install self-hosted solution on your premises                                                                                                                                                               |
| [**Dataset Management Framework**](https://github.com/cvat-ai/datumaro/blob/develop/README.md) | Specifically for the Self-Hosted version, this framework and CLI tool are essential for building, transforming, and analyzing datasets                                                                                    |
| {{< ilink "/docs/api_sdk/api" "**Server API**" >}}                                             | The CVAT server offers a HTTP REST API for interactions. This section explains how client applications, whether they are command line tools, browsers, or scripts, interact with CVAT through HTTP requests and responses |
| {{< ilink "/docs/api_sdk/sdk" "**Python SDK**" >}}                                             | The CVAT SDK is a Python library providing access to server interactions and additional functionalities like data validation and serialization                                                                            |
| {{< ilink "/docs/api_sdk/cli" "**Command Line Tool**" >}}                                      | This tool offers a straightforward command line interface for managing CVAT tasks. Currently featuring basic functionalities, it has the potential to develop into a more advanced administration tool for CVAT           |
| {{< ilink "/docs/manual/advanced/xml_format" "**XML Annotation Format**" >}}                   | Detailed documentation on the XML format used for annotations in CVAT essential for understanding data structure and compatibility                                                                                        |
| {{< ilink "/docs/administration/basics/aws-deployment-guide" "**AWS Deployment Guide**" >}}    | A step-by-step guide for deploying CVAT on Amazon Web Services, covering all necessary procedures and tips                                                                                                                |
| {{< ilink "/docs/faq" "**Frequently Asked Questions**" >}}                                     | This section addresses common queries and provides helpful answers and insights about using CVAT                                                                                                                          |

<!--lint enable maximum-line-length-->

## License Information

CVAT includes the following licenses:

<!--lint disable maximum-line-length-->

| License Type                                           | Applicable To          | Description                                                                                                                                                                                                                                   |
| ------------------------------------------------------ | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [**MIT License**](https://opensource.org/licenses/MIT) | CVAT Self-hosted            | This code is distributed under the MIT License, a permissive free software license that allows for broad use, modification, and distribution.                                                                                                 |
| [**LGPL License (FFmpeg)**](https://www.ffmpeg.org)    | CVAT Online and Self-hosted  | Incorporates LGPL-licensed components from the FFmpeg project. Users should verify if their use of FFmpeg requires additional licenses. CVAT.ai Corporation does not provide these licenses and is not liable for any related licensing fees. |
| **Commercial License**                                 | CVAT Self-hosted Enterprise edition| For commercial use of the Enterprise solution of CVAT, a separate commercial license is applicable. This is tailored for businesses and commercial entities.                                                                                  |
| [**Terms of Use**](https://www.cvat.ai/terms-of-use)   | CVAT Online and Self-hosted  | Outlines the terms of use and confidential information handling for CVAT. Important for understanding the legal framework of using the platform.                                                                                              |
| [**Privacy Policy**](https://www.cvat.ai/privacy)      | CVAT Online                  | Our Privacy Policy governs your visit to <https://cvat.ai> and your use of <https://app.cvat.ai>, and explains how we collect, safeguard and disclose information that results from your use of our Service.                                  |

<!--lint enable maximum-line-length-->

## Contacts

To contact CVAT.ai, you can use one of the following channels:

<!--lint disable maximum-line-length-->

| Support Channel                                                                                    | Applicable To         | Description                                                                                          |
| -------------------------------------------------------------------------------------------------- | --------------------- | ---------------------------------------------------------------------------------------------------- |
| [**Discord Channel**](https://discord.gg/S6sRHhuQ7K)                                               | CVAT Online and Self-hosted | A space for broader discussions, questions, and all things related to CVAT                          |
| [**LinkedIn**](https://www.linkedin.com/company/cvat-ai/)                                          | CVAT Online and Self-hosted | Follow for company updates, news, and employment opportunities.                                      |
| [**YouTube Channel**](https://www.youtube.com/@cvat-ai)                                            | CVAT Online and Self-hosted | Find tutorials and screencasts about CVAT tools                                                     |
| [**GitHub Issues**](https://github.com/cvat-ai/cvat/issues)                                        | CVAT Online and Self-hosted | Report bugs or contribute to the ongoing development of CVAT                                        |
| [**Customer Support Channel**](https://youtrack.cvat.ai/form/447d9c98-ab4b-466e-bf9d-004f01b22f73) | CVAT Online (Paid Users)    | Exclusive support for CVAT Online paid users                                                      |
| [**contact@cvat.ai**](mailto:contact+github@cvat.ai)                                               | CVAT Online and Self-hosted | For direct commercial support inquiries|

<!--lint enable maximum-line-length-->
