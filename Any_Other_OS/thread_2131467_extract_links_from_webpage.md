---
title: "extract links from webpage"
date: 2013-04-01
forum: Any Other OS
---

### Post by Si1414 on 2013-04-01
I have a "source.txt" file which contains list of some URLs. For example:


```
source.txt:    
http://www.amazon.com/gp/product/B007OZNZG0/ref=s9_pop_gw_g349_ir05/176-5131847-6150405?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=02R1PYSDAPM8P0XF7HXW&pf_rd_t=101&pf_rd_p=1263340922&pf_rd_i=507846
http://www.amazon.com/gp/product/B0083PWAPW/ref=s9_pop_gw_g424_ir04/176-5131847-6150405?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=02R1PYSDAPM8P0XF7HXW&pf_rd_t=101&pf_rd_p=1263340922&pf_rd_i=507846

```

I want to extract all links from the above URLs which contain **"/gp/product"** and then store them in "extracted.txt" file, which would be:


```
extracted.txt:
http://www.amazon.com/gp/product/B008GFRB9E/ref=fs_j
http://www.amazon.com/gp/product/B008GFUA4C/ref=fs_2

```

[I]I am using Cygwin on Windows 7 (64 bit).

[/I]Thank you for your help.

---

### Post by sisco311 on 2013-04-01
Assuming that each URL is on a separate line in the source file,  you could use grep to do the job. Do you have grep installed in your Cygwin environment?

---

### Post by Si1414 on 2013-04-01
Thank you. Yes, I have it installed on Cygwin.

---

### Post by Si1414 on 2013-04-02
I have grep installed on Cygwin. However, I want to **retrieve each links inside** "source.txt" and **search through the html** for**"/gp/product"** and store the links in "extracted.txt".
Any suggestions for this?

---

### Post by schragge on 2013-04-02
Do you mean something like
```
wget -q -i source.txt -O-|grep '/gp/product'
```
wget takes links from source.txt, downloads a HTML page for each link and feeds them to grep.

---

### Post by Si1414 on 2013-04-02
Exactly! Great Help again schragge. I really appreciate that.

---

