---
title: "MacOnLinux"
date: 2005-09-28
forum: Apple PPC Users
---

### Post by MArco_ubuntu on 2005-09-28
hi !
I try to compile mol-modules :
I have made :
~$ apt-get install mol mol-modules-source
~$ cd /usr/src
~$ tar -xvzf mol-modules.tar.gz
~$ cd linux
~$ make-kpkg modules_image

But this last command say error whit :

[cut]
make[1]: Entering directory `/usr/src/modules/mol'
/usr/bin/make -f debian/rules binary-mol-modules
make[2]: Entering directory `/usr/src/modules/mol'
dh_testdir
make[2]: dh_testdir: Command not found
make[2]: *** [build-stamp] Error 127
make[2]: Leaving directory `/usr/src/modules/mol'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/mol'
Module /usr/src/modules/mol failed.
Hit return to Continue
thanks in advance!
Marco

---

### Post by DJ_Max on 2005-09-28
Did you take a look here?

---

### Post by refdoc on 2005-09-29
[QUOTE=DJ_Max]Did you take a look here?[/QUOTE]
DJ_max - why do you link spam? This is a serious question above and the link to your completely incoherent and rather irrelevant blog does not illuminate the question.

---

### Post by DJ_Max on 2005-09-29
My bad, I meant to link to [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)
I must didn't copy and paste right. BTW, I didn't link to my blog, those links are in my sig.

---

### Post by lao_V on 2005-09-29
The link to his blog is part of his signature along with the wiki, tldp and ubuntu manual. Either he is asking the OP to look at one of those or he is asking to search on the forum? Either way, I don't think he is linking "spam" as such.

---

### Post by jansarlu on 2005-09-29
please, tell me people, how to install ubuntu on my mac. I did the partition on my mac mini dividing hd into to 2, 15 and 20 GB, and was going to install it on the 15 GB side. For some reason it could not install the base system. I ran the check on the cd-rom and it was confirmed to be ok. there was also this issue, that the installing program wanted me to do the partition also on that side and I kinda lost the whole point of that one too. So if somebody could provide me and probably others as well with moran-instructions how-to-install ubuntu on mac mini, it would be appreciated highly, for I tried this ubuntu on live-cd and I think it is great and of course furthermore free, I absolutely second this system fully.:confused:

---

### Post by domesticatewhat on 2005-09-29
I am not positive if this is true for ubuntu but I think you have to install linux on the back partition. OSX needs to be on the first partition and then format the other as free space. 

When you install ubuntu choose use largest free space and everything should go smooth from there.

If not - check if your CD is burnt correctly.

---

### Post by stuporglue on 2005-09-29
Putting this thread back on topic of the orriginal post...

[QUOTE=MArco_ubuntu]hi !
I try to compile mol-modules :
I have made :
~$ apt-get install mol mol-modules-source
~$ cd /usr/src
~$ tar -xvzf mol-modules.tar.gz
~$ cd linux
~$ make-kpkg modules_image
But this last command say error whit :
...
[/QUOTE]

Hey there, if you follow this wiki page step by step, it should probably work. Despite what it says about newer sources not having to patch the kernel headers, I still had to. Try starting over and doing every step, and see how it works out. 

[https://wiki.ubuntu.com/MacOnLinuxHowto/](https://wiki.ubuntu.com/MacOnLinuxHowto/)

Stuporglue

---

### Post by Ptero-4 on 2005-09-30
AFAIK. OSX doesn't need to be in the first partition. It's on the older iMacs where OSX (and also Linux) needs to be within the first 8GB of the HD and they don't need to be in the first partition, they only need to be in any partition that ends before or in the 8GB limit and that's only in the earlier iMacs.

---

