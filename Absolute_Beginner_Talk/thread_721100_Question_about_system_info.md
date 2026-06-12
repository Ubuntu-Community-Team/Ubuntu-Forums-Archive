---
title: "Question about system info ?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by WILL_CHAN on 2008-03-11
I just want to know what kind of OS Ubuntu I'm currently using ( 64Bit and 32Bit ). By google I got the instruction show me that I need to type in the command : " uname -a ". And then I tried it, it show me this message :
> 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linu 
Anyone could help me explain this ? I still don't know I'm using 64bit or 32bit :( ? Thanks in advance T_T !

---

### Post by jordanmthomas on 2008-03-11
```
uname -r
```
shows you the current kernel you're running.
Yours is 
```
2.6.22-14-generic
```

I'm sort out of the loop about Ubuntu-specific stuff nowadays, but that seems like you're just running the stock 32-bit kernel.  

The i686 part also gives it away I think.
```
uname -m
``` will show x86-64 or AMD64 if you were running a 64-bit kernel, but yours appears to just be i686.

What processor do you have?
```
cat /proc/cpuinfo | grep "model name"
```

---

### Post by Red Shift on 2008-03-11
You are using 32-bit Ubuntu.

---

### Post by WILL_CHAN on 2008-03-11
Thanks a lot guys. I actually need to figure this because I want to install CodeBlock 8.02. But no matter what I tried from google searching, It still not working :(.
I download the Binary version 32bit, and then extract on my Desktop. Following some instruction from one of the thread in this forum, First I created a folder name "CodeBlock", I copy all the file in the version that I downloaded from CodeBlock webstie into that folder. And then I tried : 
>  ./configure  But the terminal tell me :
> bash: ./configure: No such file or directory
 
I also tried double click on those files in order to activate it install like Window ( this step I'm not sure it work ), The package installer run for 2 seconds then it showed me the error message :
> Error : Dependency is not satisfiable : codeblocks 
Anyone could help me out to install this IDE T_T ! I'd appreciated that. Thanks in advance !

---

### Post by WILL_CHAN on 2008-03-11
I'm currently running : >  AMD Athlon(tm) 64 Processor 3700+ --> from your command T_T !

---

### Post by Red Shift on 2008-03-11
I went to [http://www.codeblocks.org](http://www.codeblocks.org), downloaded the binary release for 32-bit Ubuntu and extracted the tar archive.  All the files are .debs that can be installed by right clicking and choosing Ubuntu package menu --> install (I have Kubuntu therefore I don't know if Ubuntu has this).

Alternatively, extract all .deb files to the CodeBlock directory on your Desktop.  Change current directories to the CodeBlock directory on your Desktop.  I assume your login name is WILL_CHAN and the CodeBlock directory is located on the Desktop.  In terminal, type:
```
cd /home/WILL_CHAN/Desktop/CodeBlock
```
To unpackage and install every .deb file in CodeBlock type:
```
sudo dpkg -i *.deb
```
You will be prompted for your password.

You will need different directions if you want to install from source.  That involves ./configure.

---

### Post by jordanmthomas on 2008-03-11
This link may be of some help to you.
[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

It'll install the *latest* version (which I'm assuming is newer than what you're going for)

If you want, we can help you install what you've downloaded.  Did you download your file from here?
[http://www.codeblocks.org/downloads/5#linux](http://www.codeblocks.org/downloads/5#linux)

If so, it seems like you need to extract that file (right click and extract it)
Then, open a terminal and type this:
```
sudo dpkg -i 
```
and drag the .deb file you just extracted onto your terminal.  Then, hit enter.  It should install or at least tell you why it can't if it fails.

Don't worry about having a 64-bit processor running a 32-bit kernel.  As long as you don't have more than 4 GB of RAM you'll likely not notice a difference.

---

