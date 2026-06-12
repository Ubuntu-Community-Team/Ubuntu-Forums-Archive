---
title: "Are application installs always like this?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Scrif on 2006-05-30
Hello,

Just started using Linux (Ubuntu) and although I knew it wouldnt be easy to learn a new OS, Im a little frustrated.

I wanted to install Snort IDS. Here is what I have done:

1) downloaded Snort
2) Thru searching, figured out I had to shell to extracted file dir and run ./configure
2a) ./configure said "no acceptable C compliler"
2b) googled and found "sudo apt - get install build-essential" (no idea what this does - but it seemed to work)
2c) ran ./configure again in Snort dir
3) Snort said "go get Libpcap"
4) Got Libcap - extracted and ran ./configure
5) Libpcap said "lex is insuffient - go get Flex"
6) Got Flex - ran ./configure from Flex dir
7) Ran make
8) Libpcap make said "make: yacc: Command not found"

Stopped at this point. Its a fun game Im playing with Linux, but Im getting tired.

Can someone help?

Thanks

---

### Post by aysiu on 2006-05-30
I'm assuming you need *snort* to set up your wireless internet connection and that you otherwise have no internet connection on Ubuntu.

So in answer to your question: > Are application installs always like this? No, but if you have no internet connection... then, yes!

Have you read this?
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by mostwanted on 2006-05-30
No they're not. You're trying to compile source code which isn't exactly the easiest way to install software. Take a look at this:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Scrif on 2006-05-30
Thanks for the info. It did get me a little further. 

I didnt see Snort in the package list. 

I still had to install all Flex, Libpcre, etc manually even tho they were listed in the Pkg Mgr. Not sure what the problem is. After I finished with all the other apps, I did a ./configure, make, make install on snort and it seemd to work, but when I try to run it from the cmd line I get:

snort: error while loading shared libraries: libpcre.so.0 cannot open shared object file: No such file or dir

Oh well

---

### Post by az on 2006-05-30
[QUOTE=Scrif]Thanks for the info. It did get me a little further. I still had to install all Flex, Libpcre, etc manually even tho they were listed in the Pkg Mgr. Not sure what the problem is. [/QUOTE]
You should address that instead of trudgeing on trying to install stuff by hand.

What happened when you opened synaptic, searched for snort and tried to install it?

It is in the universe repo:
[http://packages.ubuntu.com/breezy/net/snort](http://packages.ubuntu.com/breezy/net/snort)

You would need to add universe to your list if you did not see snort in synaptic.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Scrif on 2006-05-30
Azz - You da man!

In the MonkeyBlog link, it looks like the method to enable Universe packages is different - thats what I missed.


Thanks all for the help.

---

