---
title: "installing linux on amd turion 64"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by tarek on 2006-05-18
hello,

I posted 2 threads asking if someone could help to install ubuntu or kubuntu on my pc but no luck. I also searched the internet for an answer but nothing.

I have Compaq Presario V2570CA - AMD Turion 64:
[http://www.hp.ca/products/static/presario-notebooks/v2570ca/V2570CA.pdf](http://www.hp.ca/products/static/presario-notebooks/v2570ca/V2570CA.pdf)

can I install k/ubuntu on my laptop?

I tried and when i run the installation, I get the screen where I choose the default or the server installation. so I choose default, and then it loads some information on the screen and stops! it just stops doing anything... I waited for a long time but nothing.

if know how to install it on turion amd 64, please let me know what is the secret to install k/ubuntu.

and if I cannot install k/ubuntu, also let me know.....

any help is appreciated...thanks.

TK

---

### Post by Mustard on 2006-05-18
I don't know whether you have been down this road already in other threads, but I think some more information is needed to eliminate the obvious problems. Perhaps you could post links to the other threads if you have answered these questions already.

Where did you get the install disks?

If you burned them yourself, did you verify the ISO file with md5sum check?  

Following that did you verify the CD media after burning?

Once the most obvious causes of installer errors are eliminated then its possible to move on to other possibilities.  Given the symptoms described though, its not giving many clues to what that might be, ie lack of ouput on the screen showing what is failing during the install process.

-edit-

You did mention that it shows some information on the screen.  What that information is might be vital to understanding the problem should it prove that the ISO and media are not at fault.

---

### Post by tarek on 2006-05-21
I got the cd from kubuntu's site, and I ran md5sum check and I got the same string.

I took pics for the installation - used the default install, please see the attached files.

the installation pauses in the second pic...

thanks

---

### Post by Mustard on 2006-05-21
Hmmm..the pics are not giving me any clues either unfortunately.  If you press the function keys when you are at the boot prompt in the first pic, there are some special boot options you can use to try starting the installation.  Read through the instructions to see how to input those options at the command prompt and give them a try.  Ones like noapic nolapic are common options that people try.

---

### Post by macdo on 2006-05-21
Probably a stupid question, but you **are** using the 64bit version of ubuntu, aren't you?

---

### Post by tarek on 2006-05-21
[QUOTE=macdo]Probably a stupid question, but you **are** using the 64bit version of ubuntu, aren't you?[/QUOTE]


yes, I'm using the 64bit, I also tried the live 64bit cd and got the same problem.

---

### Post by tarek on 2006-05-21
[QUOTE=Mustard]Hmmm..the pics are not giving me any clues either unfortunately.  If you press the function keys when you are at the boot prompt in the first pic, there are some special boot options you can use to try starting the installation.  Read through the instructions to see how to input those options at the command prompt and give them a try.  Ones like noapic nolapic are common options that people try.[/QUOTE]

let's see, I tried "expert noapic nolapic" from this site: [http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html](http://mypage.iu.edu/~abatto/essays/Install-Ubuntu-5.10-Compaq-v2410.html)

and I did not know what to choose or to do.. I used linux as a user to program C++, php, perl but never as an administrator, so I do not know what options to choose.

If you used the expert mode before, can you please tell me the steps, I know this is a lot to ask but believe me I installed linux before on my 32bit desktop, I recently installed fedora 5 and suse 10.1 on my 64bit laptop and the installation for both was easy and worked just fine. but I like kubuntu and want to use it.

thanks again,
TK

---

### Post by Mustard on 2006-05-21
I don't think you need to choose expert to add those options.  If you do however then it will ask you for a root password and not set your first user account with sudo privileges.  It's pretty easy to change this to the default install settings though.  If you can't find the answer to doing a default install with noapic nolapic then you might try starting a new thread asking this question specifically (seeing as no-one else seems to be answering your questions in this thread.)

My recollection of the expert install options is not sufficient for me to be able to tell you the whole process step by step.

---

### Post by tarek on 2006-05-22
I installed suse linux 10.1, it detected all my hardware, except my wireless which I'm trying to fix it right now. 

I tried the expert mode again with ubuntu but did no know what to do. I guess I will wait until new version of ubuntu is out or somebody actually try to install ubuntu on turion 64bit.

any ways, thanks for the help.

TK

---

### Post by ajinkyakulkarni87 on 2007-11-26
> **tarek said:**
> hello,

I posted 2 threads asking if someone could help to install ubuntu or kubuntu on my pc but no luck. I also searched the internet for an answer but nothing.

I have Compaq Presario V2570CA - AMD Turion 64:
[http://www.hp.ca/products/static/presario-notebooks/v2570ca/V2570CA.pdf](http://www.hp.ca/products/static/presario-notebooks/v2570ca/V2570CA.pdf)

can I install k/ubuntu on my laptop?

I tried and when i run the installation, I get the screen where I choose the default or the server installation. so I choose default, and then it loads some information on the screen and stops! it just stops doing anything... I waited for a long time but nothing.

if know how to install it on turion amd 64, please let me know what is the secret to install k/ubuntu.

and if I cannot install k/ubuntu, also let me know.....

any help is appreciated...thanks.

TK

[COLOR="Purple"][B]I also have same laptop but can not install ubuntu 7.10 32bit . Ubuntu freezes during booting. 

I have searched on many forums but could not managed to run/install ubuntu 7.10.
e.g [https://answers.launchpad.net/ubuntu/+question/18029](https://answers.launchpad.net/ubuntu/+question/18029)

Any solution ?[/B][/COLOR]

---

