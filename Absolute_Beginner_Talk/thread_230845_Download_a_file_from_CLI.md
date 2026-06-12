---
title: "Download a file from CLI?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2006-08-06
How do you download a file from CLI?  I would like to get the latest Knoppix ISO file but it uses too much bandwidth.  I wonder if I can do this with the sleep command from the CLI?

Any ideas?

---

### Post by wombat20 on 2006-08-06
Errr, normally people use wget for this don't they?  Sorry I don't know the exact syntax.

---

### Post by Lord Illidan on 2006-08-06
Type ```
man wget
``` into a terminal.

---

### Post by Jagot on 2006-08-06
For me to download the Knoppix iso from the mirror I use, in Terminal I would type:

```
wget ftp://ftp.mirrorservice.org/sites/ftp.uni-kl.de/pub/linux/knoppix/KNOPPIX_V4.0.2CD-2005-09-23-EN.iso
```

---

### Post by kebes on 2006-08-06
There are three commands I use to download files from CLI: "wget", "curl", and "lynx".

lynx is a text/command-line web-browser, and you can use it to visit webpages and get the files you need. If you know the exact URL, then as an argument to curl or wget this will download the file easily.

With regard to your question, curl has an option "--limit-rate" where you can specify a limit on the download rate. (Refer to the manual page: "man curl".)

I think curl is not installed by default on Ubuntu, but it should be a simple matter to install it ("sudo aptitude install curl").

---

