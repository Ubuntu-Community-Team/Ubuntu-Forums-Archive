---
title: "Communication from Ubuntu to iPad"
date: 2012-03-24
forum: Any Other OS
---

### Post by susja on 2012-03-24
Hello,
I'm using Ubunty 11.10. Yesterday I bought iPad 3 and reading manual. It states that the only way to sync between iPad and PC is usng iTunes. Let say I need to transfer files in either direction or etc I should use iTunes. Also manual states that after I connect my device to PC in iPad iTunes app I should see Apps pane which I should use for files transfer.
In my case when I connected device to PC it recognized it as iPad and I see 2 mounted devices: iPad and 'Documents on iPad' from PC side but from iPad iTunes I don't see any Apps pane.
Could someone clarify for me what I'm doing wrong and how to use iTunes and move files using Ubuntu and iPad?
Thanks in advance.

---

### Post by susja on 2012-03-24
> **susja said:**
> Hello,
I'm using Ubunty 11.10. Yesterday I bought iPad 3 and reading manual. It states that the only way to sync between iPad and PC is usng iTunes. Let say I need to transfer files in either direction or etc I should use iTunes. Also manual states that after I connect my device to PC in iPad iTunes app I should see Apps pane which I should use for files transfer.
In my case when I connected device to PC it recognized it as iPad and I see 2 mounted devices: iPad and 'Documents on iPad' from PC side but from iPad iTunes I don't see any Apps pane.
Could someone clarify for me what I'm doing wrong and how to use iTunes and move files using Ubuntu and iPad?
Thanks in advance.

Well I realized that I have to install iTunes on Ubuntu. iTunes supports only Windows and Mac. I had to install WINE and then download and install iTunes 10 using Wine but it does not work right i.e. crash all the time.
Does anyone has good experience to install iTunes on Ubuntu?
Thanks.

---

### Post by r-senior on 2012-03-25
With iOS 5 the requirement to sync to iTunes on a PC or Mac is much reduced. iOS devices can back up wirelessly to iCloud (if you enable it) and can also be upgraded between iOS versions.

The thing you miss by not having iTunes is the capability to sync music, videos, books, podcasts, etc.

What files were you thinking? Dropbox is a good solution for sharing things like PDFs and similar.

---

### Post by susja on 2012-03-25
Thanks so much for your reply.
I will definitely try Dropbox in case iPad supports  it.
My goal is to get books, movies and etc that I have on PC and transfer it to iPad.
The current problem is that I wanted to install iTunes on my PC. I downloaded Wine and  then downloaded  iTunes 10. After I  installed iTunes it  doesn't, work right. I mean the terminal where I start iTune throws  a bunch of errors, sometime it even crashs and I can't even login to iTunes.
I think that I'll have to uninstall iTunes (don't know how to do it using Wine) and likely try to install iTunes once more time. Not sure what I did wrong first time ... Or  maybe iTunes just are not stable on Ubuntu 11.10
I think that in any case I need to have 'good'  install of iTunes as a starting point.
Thanks again and appreciate your help.

---

### Post by susja on 2012-03-25
> **susja said:**
> Thanks so much for your reply.
I will definitely try Dropbox in case iPad supports  it.
My goal is to get books, movies and etc that I have on PC and transfer it to iPad.
The current problem is that I wanted to install iTunes on my PC. I downloaded Wine and  then downloaded  iTunes 10. After I  installed iTunes it  doesn't, work right. I mean the terminal where I start iTune throws  a bunch of errors, sometime it even crashs and I can't even login to iTunes.
I think that I'll have to uninstall iTunes (don't know how to do it using Wine) and likely try to install iTunes once more time. Not sure what I did wrong first time ... Or  maybe iTunes just are not stable on Ubuntu 11.10
I think that in any case I need to have 'good'  install of iTunes as a starting point.
Thanks again and appreciate your help.

Well I read so many posts about Wine not being stable running iTune ...  that distracted me from reinstalling it. I uninstalled Wine and iTunes and installed Virtualbox. Now I'm going to install iTunes on my virtual Windows machine.
After that I'll start to play with file transfer and sync.
thanks

---

