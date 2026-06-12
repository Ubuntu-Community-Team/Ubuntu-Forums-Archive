---
title: "Static Packages"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by VON_CAPO on 2008-01-14
I really like Ubuntu and I erased the Windows partition a few moths ago.

But now I realize that each time a new Ubuntu release shows up, I must reinstall (compilate) a lot of software that is only available from source.

Also DEB packages created for Gutsy could not work or install in the next release, so, it is only matter of luck that any maintainer will show up and will create the necessary new package.  

This is a worrysome issue because there is not any guarantee that the old software will work with the new realease. 

Also, I had noticed that some software works 100% in some distros, but in others is impossible make them work without some tweaking from an expert programmer. 

The system of dynamic libraries is nice and elegant to support a selected group of applications; but out there, there is a huge universe of software very hard to compile under any specific distro without to get a lot of errors, and without the knowledge to fix them.

Because of this, is there any way to get or create Static Packages (they include all the dependencies and they will install in any future release)? :confused:

---

### Post by szymon_g on 2008-01-14
man gcc ;p

///
btw, why are you recompilling packages when you are upgrading to new release of ubuntu?

sudo aptitude dist-upgrade or something like that didn't work :?

---

### Post by VON_CAPO on 2008-01-14
> **szymon_g said:**
> man gcc ;p

///
btw, why are you recompilling packages when you are upgrading to new release of ubuntu?

sudo aptitude dist-upgrade or something like that didn't work :?

I am a relatively new Linux user. 

I just made a full migration to GNU/Linux 6 month ago, after I understood how to properly install Ubuntu and how to make work my hardware. So, my knowledge is pretty limited.

Also, in this Forum I read about issues with the upgrade, so, I did not take any chance and I made a clean installation following the same procedure I did with Feisty.

Please, do not get me wrong, if I install software from source, is because I just follow the developer's instructions, and not because I am some sort of advanced user.

And as you had written the command "man gcc","aptitude dist-upgrade", I know the first one but I can not understand the output, and the second one is unknown to me.

Because of all these difficulties, my question is:  Is there any chance to get (some repository?) or create by a regular Joe a **"static package"**?

Otherwise, I think I should recreate a NTFS partition to install M$ soft in case the Linux software stop working. :(

---

### Post by Cypher on 2008-01-14
So I take it that you are installing software that is not currently available in the Ubuntu repository (for which you could do "apt-get install"). If that is the case, with the each distribution upgrade, you might be forced to re-do the source compilation following the original instructions. In most cases, things should compile and install without any problems..

Be sure to use the "checkinstall" program which will create a DEB package for installation purposes, so you can manage it using the standard Ubuntu package manager..

---

### Post by VON_CAPO on 2008-01-14
> **Cypher said:**
> So I take it that you are installing software that is not currently available in the Ubuntu repository (for which you could do "apt-get install"). If that is the case, with the each distribution upgrade, you might be forced to re-do the source compilation following the original instructions. In most cases, things should compile and install without any problems..

Be sure to use the "checkinstall" program which will create a DEB package for installation purposes, so you can manage it using the standard Ubuntu package manager..
Ok, I googled "checkinstall" and after I got the checkinstall's home page, I found the documentation's page. ---> [http://asic-linux.com.mx/~izto/checkinstall/docs/README](http://asic-linux.com.mx/~izto/checkinstall/docs/README)

WOW! If I understood correctly, it is a **MANUAL**, step by step about how to create a DEB file. :):):)

I do not know if with this I can create a "static package", but I think it is a beginning towards the solution.

Cypher, you gave me "gold".
Thank you so much!!! :popcorn:

---

