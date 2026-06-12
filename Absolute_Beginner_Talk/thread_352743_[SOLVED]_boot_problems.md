---
title: "[SOLVED] boot problems"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-02-03
The first thing I did was install Ubuntu 6.06. Every thing went well. I was so happy I decided to install Kubuntu also. (at the time I didn't know you could do that from within Ubuntu) The Kubuntu install went well also except now grub (newly installed with Kubuntu) wouldn't start Ubuntu. Then everyone told me that I didn't need both, so not knowing yet how to fix grub, I reinstalled Ubuntu. 

Then Ubuntu was fixed, but I kinda expected Grub (newly installed with Ubuntu) to see the Kubuntu install as another Linux OS. It didn't though, but that was no big deal since it was already pointed out that I didn't need both.

So, then I decided to also try Fedora. The install went well and since Fedora also uses Grub, not knowing any better I let it install Grub again. So when I rebooted Fedora it started right up but there was no mention of Ubuntu or Kubuntu.

I then learned how to edit Grub but I didn't like the menu.lst that came with Fedora (Ubuntu's had instructions and looked easier for newbies like me) So, I reinstalled Ubuntu again so it would control Grub.

Now, I copied the text from menu.lst in the Fedoras grub folder and pasted it into the menu.lst of Ubuntu's menu.lst and Fedora started to boot.

But then It reached a point where it hung up at "starting bluetooth services".

I tried reinstalling Fedora without reinstalling grub. same result.

Just to satisfy my curiosity I pasted the Kubuntu menu.lst into Ubuntu's menu.lst and it started to boot but then hung up at "Starting Bluetooth Services".

Ubuntu still boots just fine, and by the way so do my copies of windows,but Kubuntu and Fedora will not.

Anybody know what this is? Thanks in advance for your help

---

