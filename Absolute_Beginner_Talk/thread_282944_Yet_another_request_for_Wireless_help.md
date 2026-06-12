---
title: "Yet another request for Wireless help"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Mortimer5 on 2006-10-23
I know everyone asks this, but how can I get Ubuntu 5.10 to work with my laptop's wireless setup? The card doesn't show up under the possible network connections, so from what I've gathered that meants I need to find the driver. The problem is, I have no idea where to find the right driver and how to install it.

According to Windows, what I have is an Intel PRO/Wireless 3945ABG network connection.

Thanks in advance for any assistance you can give.

---

### Post by dbott67 on 2006-10-23
You can try [here]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21").

Installing Intel(R) PRO/Wireless driver for Linux:
- Extract the archive driver file: tar xzvf ipw3945-linux-1.0.0.tgz
- The following is needed to install the driver:
1. Linux OS with a 2.6.13+ kernel. See ./ipw3945-1.0.0/README.ipw3945 for
specific details.
2. The driver files (ipw3945-1.0.0.tgz) 
3. The binary Ucode image (ipw3945-ucode-1.13.tgz)
4. The regulatory daemon binary (ipw3945d-1.7.18.tgz)
5. For instructions on how to build and use the driver, please refer to 
the INSTALL document in the ./intel_ipw3945-1.0.0/ directory.

---

