---
title: "First Impressions"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by yacahuma on 2006-08-09
People say that first impressions last a life time.  I hope this is not the case with ubuntu. I was a linux unix user before version 1 and I have seen from the sidelines how it changed and mature.  I have to say I am a little disapointed.  The reason I am looking for and alternative is because I am really getting tired of windows xp and  having to reinstall the OS every now and then because it is too slow. 

Now to the subject at hand.  The first thing I tried was to install ubuntu on vmware workstation under windows xp.  The problem, it alwsy got stock when selecting the timezone. I had to go to compusa and buy some 700MB cd. I have a pile of 650MB and it will not fit.

Suggestion #1:
Make it fix on a 650MB CD and download any remaining packages at a later time.

I have a 250GB HD and I allocated 30GB for the ubuntu trial.  I went ahead and try to do a normal install after my failure with vmware.  Even though I created a swap partition with type (linux swap) it will not allow me to select the mount point /hdb7. Even though the partition was created. 

Problem#1: Could this be a bug??? I will have to create the swap partition manually. This is something a normal user will not be able to do.Remember I am looking at this from a windows XP replacement point of view.

After selecting just one main partition the software installed without any problems except that now I get GRUB when the machine boots.  

Problem #2: I never authorized any change to my MBR. Back in the days of redh hat 1, the installation asked me if I wanted to install the boot on the MBR or in the boot sector of the installation drive/ If I had 2 drive, my windows section will never be touched. I just used the BIOS for booting different OS. I know extra work, but it is effective. 


After the unauthorized change to my system, the OS booted fast and nice looking. Cool.  The system alerted me to run the update 160 updates. After that my first surprise, the system asked to to restart. WHAT? back in the days the only restart was after rebuilding the OS.:confused: 

I fired firefox and visit news.com.  I try to watch cnet tv. it asked me to install flash.

Problem #3: the flash install asked me to extract the files and run a script from the command line. I am not really sure what is involve here but if we want people moving to linux for every day work, you cannot asked them to run a script from a command line.NO NO. When I ran the script it is telling me that I need gsfont and gsfonts-x11

And thats were I am right now.  I stiil need to create the swap and mofify fstab and see where can I find the gsfonts.  Also as a PHP developer and was wating for and easy install of server packages(apache,mysql, etc).  I see some apache files in the Package manager but not the apache server.

Suggestiong #2: It will be good to have Server section on the package manager with programs like ftp, apache, mysql, postgre, etc. You get the idea.

I will keep playing but the "Linux Desktop" still a few years away.  I hope that my suggestions and first impressions help make this distribution a better one.

---

### Post by GuitarHero on 2006-08-09
Almost all of your problems are solveable.  Also this thread should have been in ubuntu testimonials under ubuntu cafe.

---

### Post by nalmeth on 2006-08-09
First impressions aren't always fair when a distributition dedicated to freedom is forced to follow certain *restrictions *with *restricted *software.

I don't know anything about your vmware or apache/server problems.

You were asked to reboot, likely because you upgraded the kernel.

2 links you should check out:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

[http://doc.gwos.org/](http://doc.gwos.org/) (Ubuntu Document Storage Facility)
and/or
[http://wiki.ubuntu.com/community]("http://wiki.ubuntu.com/")

---

### Post by yacahuma on 2006-08-10
nalmeth, Thank you for your help. automatix is just what the doctor order.  Now I am on my way to ubuntu freedom. 


Guitar Hero,  I now the problems can be solved, but that is not the point. In my position I have can suggest which platform my company is going to use.  If I can use , ubuntu for my every day work, I could move subtancial amount of pc to this OS. My suggestions are targeted toward this. Have the possibility of moving normal people to another OS with minimal impact.  All I am saying is that this are very basic things that should be fix. These problems increase your TCO and is Microsoft argument everytime.

---

### Post by aysiu on 2006-08-10
Occasionally we do get people (yours is probably the second post I've read about this--and I've read **a lot** of threads) who bemoan the CD size being bigger than 650 MB, but I'm sorry... Ubuntu isn't going to change that for you and the other person who had to go buy a 700 MB CD.

Ubuntu will ship you CDs for free (including postage) if you're too poor to afford the US$1 (or less) cost of a 700 MB CD.

A lot of thought goes into creating the Ubuntu CD and deciding which packages get included. They would have to cut out a lot more to whittle it down to 650 MB. Don't forget, too, that the **Desktop CD** is a live CD... so it's not just a matter of downloading extra packages.

In other words, I strongly disagree with your suggestion. You're talking about inconveniencing the many (the Ubuntu users and the Ubuntu servers) to download a few extra packages to make it more convenient for the few (who have the bandwidth and broadband and burner to burn Ubuntu themselves but who also have only 650 MB CDs).

---

### Post by wpshooter on 2006-08-10
Yacahuma:

I agree with you that this O/S is a while away from being friendly enough for most normal people/users.  If you like your job and eating regularly, you had probably better wait (say 2 to 3 year) before you recommend that your company adopt Ubuntu for production work.

As you critique it, you may want to pass your suggestions on to the people that are doing the development of Ubuntu.  

I don't believe that they pickup on suggestions posted on this forum or at least not in normal posting sections.  Might want to try stickys or look around for other avenues for suggesting improvements.

Thanks.

---

### Post by yacahuma on 2006-08-10
calm down kid. My comments was that I had to go out and buy it because all I got was 650MB. Its been a long time since I bought cds and at the time, thats all they have. I wanted to install it as soon as posible and having to go out was an inconvenience. In any case, I can't imagine that dumping 50MB will be a big deal.650MB should be more than enough. Hey , but thats just me!!. No big deal.

---

### Post by aysiu on 2006-08-10
> **yacahuma said:**
> calm down kid. What makes you think I'm not calm? What makes you think I'm a kid? > 650MB should be more than enough. Hey , but thats just me!! At least we agree on one thing--it is just you.

---

### Post by yacahuma on 2006-08-10
I think I found why I cant watch cnet tv.  They are using flash 8 and adobe says that they are waiting for a flash 8.5 before releasing it to the linux community.


In terms of the linux desktop, what bothers me most is that all the code seems to be there. It just need a little bit more finishing work.

---

### Post by davebgimp on 2006-08-10
> **yacahuma said:**
> In terms of the linux desktop, what bothers me most is that all the code seems to be there. It just need a little bit more finishing work.

Gee...maybe that's why a new release comes out every six months?

---

### Post by yacahuma on 2006-08-10
aysiu.   I like your attitude.  We should go and drink someday. Beers on me.

---

### Post by aysiu on 2006-08-10
> **yacahuma said:**
> 
In terms of the linux desktop, what bothers me most is that all the code seems to be there. It just need a little bit more finishing work. In terms of the Linux desktop, read my signature.

---

### Post by anaconda on 2006-08-10
> Suggestion #1:
Make it fix on a 650MB CD and download any remaining packages at a later time.


Interesting suggestion! 
I have Quite the opposite problem. I dont have empty CD:s anymore, because empty CD costs about 1$, BUT empty DVD costs only about 0,30$, So why would I by CD:s ??

However, I wouldn't want to download 4GB data for an ubuntu DVD.. because it would take ages to download. I would just want to have a DVD-image, which would be the same 700MB than the CD-version.

---

### Post by aysiu on 2006-08-10
I don't know the details of this, but I think I read a thread indicating that there was a way to burn the CD ISO image to a DVD and have it work.

---

### Post by anaconda on 2006-08-10
> 
I don't know the details of this, but.. 

Thats a pity..
If you remember where you read about it I would be VERY interested..

---

### Post by aysiu on 2006-08-10
If I find it, I'll post the link back here.

---

### Post by nalmeth on 2006-08-10
There must be a special procedure to do that aysiu, as it doesn't work with simply burning it.

About the flash 8 problem, believe it or not you can run firefox or IE6 with flash 8 in wine.

[http://www.howtoforge.com/ubuntu_flash_player](http://www.howtoforge.com/ubuntu_flash_player)

To get IE6, there is a script called ie4linux that will do all the work for you.

---

### Post by wpshooter on 2006-08-10
> **anaconda said:**
> Interesting suggestion! 
I have Quite the opposite problem. I dont have empty CD:s anymore, because empty CD costs about 1$, BUT empty DVD costs only about 0,30$, So why would I by CD:s ??

However, I wouldn't want to download 4GB data for an ubuntu DVD.. because it would take ages to download. I would just want to have a DVD-image, which would be the same 700MB than the CD-version.

Buy yourself a few good high qualiy CD-RWs and use them over, & over & over again for Ubuntu burning or whatever strikes your fancy.

---

### Post by Drakkor on 2006-08-10
Good idea, I burned mine on a rw,and had to reburn it because of an error,but I used the same disk,so no waste,which is great to think about when you consider all the coasters in the landfills,lol. My experience with Ubuntu was and is still great,considering this forum in my opinion is one of the best on the net, and people here will help you with any snag you may encounter. Over the years I have tried various linux distros,but Ubuntu probably is my favorite,because it just seems to work so well,true,there's a little learning curve, but once it's properly set-up,it's amazing,and you need very little command line input unless you choose to do so ! Keep with it ! Two months now and the only reason I even use XP is to make an Acronis True Image backup of my Ubuntu drive, in case I mess something up ! :p

---

