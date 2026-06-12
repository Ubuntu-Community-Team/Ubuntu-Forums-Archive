---
title: "how to start with opencl acceleration enabled"
date: 2012-08-31
forum: Art &amp; Design
---

### Post by vanangamudi on 2012-08-31
how to start gimp with opencl features of gegl enabled. I'm using gimp2.8.2 in ubuntu12.04

---

### Post by vertago1 on 2012-10-24
Ubuntu 12.10 includes GIMP 2.8.2 which has support for OpenCL acceleration.

According to their website you must run:
> GEGL_USE_OPENCL=yes
to enable the support.

I wanted to give it a try but I wanted to know how I could tell whether or not it actually was working. It would be helpful to know what additional libraries need to be installed such as AMD's opencl SDK for AMD video devices, nvidia's opencl support, etc.

Does anyone have any experience getting this to work?

---

