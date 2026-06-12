---
title: "Not sure of problem"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by shashank103 on 2007-09-12
I installed UBUNTU 7.04 (Fiesty) on my computer with configuration 
    AMD athlon 3000+ 
    ASUS A8V-VM  (with VIA/S3G DELTACHROME IGP)
    RAM 1 gb

there was no problem during installation and i didn't install any  linux drivers of my mobo , now whenever i try for enabling desktop effects , whole screen will become white for 4-5 minutes and then it will again come to it's normal state without enabling desktop effects .
     in restricted driver manager it shows that _**"  there is no need of restricted driver for your hardware"_**   .
             I searhed for the graphic driver of my mobo , but i didn't get because according to me the via hasn't introduced the deltachrome drivers for linux . 
                          if there is any way to solve these problems plz help me ........................

---

### Post by Terl on 2007-09-12
I searched a bit using google and found lots of bad news.  Apparently there are many folks like you looking for drivers for this card.  I had to use babelfish to translate some of this stuff, but it seems as if there are no linux drivers for that card.

Do you have the exact model number perhaps?  That would help find more info.  If I were you I would google some more for the card and model; add a + linux in the search to narrow it down a bit.

Remember too that the manufacturers need to support linux.  If I were you I would definitely let Via know you are looking for drivers.

Bottom line, until you can find some good drivers you will probably have to stay with the generic VESA driver.  The other option, if possible, is to get a graphics card if your mobo supports such.

---

### Post by Kobalt on 2007-09-12
There are opensource drivers for such chipsets, they are called OpenChrome. Here is how to install them : [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

I'm not sure of the possibility to have desktop effects though...

---

### Post by shashank103 on 2007-09-12
Thanks for the help ,I have seen this open chrome drivers for via but  it's only for unichrome chipset but mine is deltachrome chipset .............  ...... if any body know driver provided by anybody else other than via which can run properly ...plz tell me...or people wid same mobo ...........how did they solve this problem

---

