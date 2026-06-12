---
title: "TrueCrypt installation problems Ubuntu 10.04"
date: 2010-09-15
forum: Apple Hardware Users
---

### Post by Iecur on 2010-09-15
Okay so I'm new to the world of Linux and Macs so please bear with me.

I recently received an old 17" PowerBook G4.  Which felt a bit weird seeing as I've been on Windows for so many years.  I figured this could be my chance to try out Linux for more than just ten seconds then uninstall it.  To my surprise I've kept up with it for a while now figuring out how to get a few programs to compile has been a bit challenging here and there but I've eventually figured out how to get them to run.

Now to my problem.  Whenever I try to install TrueCrypt.  I've tried versions 7.0/a and I always get this message when trying to compile:
~/truecrypt-7.0a-source/Common/SecurityToken.h:43:21: warning: pkcs11.h: No such file or directory
And I have been to google searching like a madman.  How I've searched..I've found threads here and there with no success.  There was one thread that I found where someone mentioned how to get it to work and they would write up a guide on how to accomplish getting the installation to get past that but I haven't been able to locate said guide.  I don't know maybe I'm just too tired and if someone sees it or knows the answer and it should of course be obvious to anyone please be kind enough to share your knowledge with me. 

If there is any information that I have careless left out please let me know so that I can try inform you of whatever I have forgotten to mention.

Also if this thread is in the wrong forum I'm hoping someone can help me place it in the right one.  Wasn't too sure if it was an issue to do with this computer using the Power PC architecture or not.  And seeing as there are downloads for Linux in the 32-bit and 64-bit flavours and a lack of threads at least via google asking for support of the installation with TrueCrypt I decided to put it here.

Thanks for taking your time to read this and any help that you may be able to provide to me.

---

### Post by endotherm on 2010-09-15
you shouldn't need to compile truecrypt (they supply an installer that works with ubuntu), but if you feel you must, what commands did you issue to do so? did you remember to run .configure?


before compiling, did you install the build-essentials and the kernel-headers? 


if you don't want to compile, just download the correct version for your hardware (x64/x86 console or gui) and extract it. then in a terminal 'cd' to the location where the extracted file is. then issue a command like this one (but calling the specific installer script you downloaded)
```
sudo sh ./truecrypt-7.0a-setup-x86
```and voila

---

### Post by Iecur on 2010-09-15
Hmm..how would I find out whether I'm running x64/x86 hardware ?  I've never really worked with Macs and somehow got the idea that the architecture was totally different and therefore installing said types of programs wouldn't exactly run or install on here.

Oh right and as for the before compiling thing.  I believe I have installed everything but the last ones:
"- RSA Security Inc. PKCS #11 Cryptographic Token Interface (Cryptoki) 2.20
  header files (available at [ftp://ftp.rsasecurity.com/pub/pkcs/pkcs-11/v2-20](ftp://ftp.rsasecurity.com/pub/pkcs/pkcs-11/v2-20))
  located in a standard include path or in a directory defined by the
  environment variable 'PKCS11_INC'."
I seriously couldn't figure out what the heck to do there.  I downloaded the pkcs11.h and whatnot files but with no clue what to do I tried looking for the files in the Synaptic Package Manager with no avail.  And like I said on the first post.  I kept trying to search around for instructions on what to do but no one talked about it but on one thread I found where someone said they figured out what to do but didn't specify what to do.

---

### Post by prshah on 2010-09-15
> **Iecur said:**
> 
  located in a standard include path or in a directory defined by the
  environment variable 'PKCS11_INC'."

Try adding ```
PKCS11_INC=/home/yourdir/pkcsheaderdir/
``` before the command use to compile, separated by a space, eg```
PKCS11_INC=/home/yourdir/pkcsheaderdir/  make
```

Or you can issue a separate command as```
export PKCS11_INC=/home/yourdir/pkcsheaderdir/
``` and then issue your compile command.

Replace /home/yourdir/pkcsheaderdir/ with the directory where your downloaded the header (.h) file.

---

### Post by Iecur on 2010-09-15
Well, that did it.
Thank you very much!

Only thing is I have a few more questions but I don't know if I should either leave that for a different thread and just leave this one as solved or to change the title of this thread into something like "endless list of things Iecur needs help with" because I will be back that is for sure.  

Well, looks like I can finally get some sleep...Good night all and again thanks a lot prshah this one was driving me nuts.

---

### Post by prshah on 2010-09-16
> **Iecur said:**
> just leave this one as solved or to change the title of this thread into something like "endless list of things Iecur needs help with"

I would suggest you leave this as solved, and open a new thread for other problems not specifically related to this one.

This is because when others like you search for help on this topic, they will find this quickly, but if you dilute it by asking other questions, I do believe it will lose relevance in search rankings.

But ultimately, it's your thread, your decision!

---

