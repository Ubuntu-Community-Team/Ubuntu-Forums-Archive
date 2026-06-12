---
title: "Wireless and ALSA not working"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Mydrid on 2007-02-10
OK, this may seem a bit rash, considering I am only at day 2 with Ubuntu. I can't get ANYTHING to work properly. I can't get ndiswrapper to install, despite following VERY detailed instructions aimed specifically at Ubuntu. Apparently, in fact, Ubuntu is supposed to have ndiswrapper in the kernel by default. Mine doesn't! So I have no internet, as my wireless adapter can't work without Ndiswrapper (or so I hope). Now I am trying to install the new Alsa module to support my EMU 1820m soundcard. Again, despite following EXACT instructions, nothing works. All I have done is installed a fresh copy of Ubuntu on my system and have not had any joy getting anything to work since! Do I have some kind of retarded version which does not allow anything to work as it should, or are the ALSA and Ndiswrap packages just rubbish? Oh. I nearly forgot. I have also tried to install Xine (lib & ui) and the libcss package, with nothing but error messages. Again, of course, following detailed instructions. I am going insane. I have spent so many hours typing lines of code that my brain hurts. That ould be fine if I had ANYTHING at all to show for my work. But I don't. Any suggestions, other than that I simply must be doing everything wrong, would be greatly appreciated.

---

### Post by Perfect Storm on 2007-02-10
I have changed the title to someting more useful and to avoid unpleasentness as some people take it as a flamebait.


best regards
A.I. Dude

---

### Post by pay on 2007-02-10
Saying that something doesn't work doesn't help us to know why it doesn't work. What errors are you getting? What guides are you following?...

---

### Post by Mydrid on 2007-02-10
All good points. I did not mean to offend at all, the title was more of a joke than anything. I have no clue what the issues are, to be honest. Basically, I am firstly confused as to why I have read that Hoary has ndiswrapper 1.0rc2 in the kernel by default, but my release (edgy, I beleive) has no trace of it. The guide I am using is from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu) . This seemed to be the most comprehensive guide. At the point of 'prerequisites, my system falls flat on its' face. There is no link  to the kernel source from the modules directory. So I create one, exactly as it says. Then I try to follow the install steps. I get so many errors, I can't list them all. From memory, there is an error stating that it cannot create a directory. Possibly something about file permissions (despite using SUDO command). It is difficult to know where to start pointing out the errors, because errors are all I can muster. I am sure the fault lies with me, but how can I be failing at following instructions. They are simple enough. Any ideas? Especially regarding whether ndiswrapper should be already on my system. I am surprised that there is no .run file or some similar executable package file to sort out the ndiswrapper install. It seems a very popular program. Thanks for the help.

---

### Post by pay on 2007-02-10
sudo needs to be lowercase. Also check if your card is even supported [here](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and [here](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported). Also try [this](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) guide as its aimed at edgy. I haven't actually used it since I don't have a wireless card. For your dvd problem, look [here.](https://help.ubuntu.com/community/RestrictedFormats)
Good luck.

---

### Post by Mydrid on 2007-02-10
I know it needs to be lower case, I just wanted it to stand out in the post, to show that I had attained super user. Thanks anyway.

---

### Post by Mydrid on 2007-02-10
With regards to ASLA, I am following the instructions at [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1820m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1820m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga) .

Again, I am doomed from the word 'go'. I can unzip the driver without issue. When I get to the ./configure --with-cards=emu10k1-fpga --with-sequencer=yes;make;make install command, it presents a plethora of errors for me. Why is the first step on the instructions messing up, when I am using a fresh installation of Ubuntu? Surely the instructions apply to the default kernel? Would changing to the 'Dapper' release help my cause at all? Thanks.

---

### Post by pay on 2007-02-10
> **Mydrid said:**
> With regards to ASLA, I am following the instructions at [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1820m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1820m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga) .

Again, I am doomed from the word 'go'. I can unzip the driver without issue. When I get to the ./configure --with-cards=emu10k1-fpga --with-sequencer=yes;make;make install command, it presents a plethora of errors for me. Why is the first step on the instructions messing up, when I am using a fresh installation of Ubuntu? Surely the instructions apply to the default kernel? Would changing to the 'Dapper' release help my cause at all? Thanks.Again, I can't tell you why it isn't working without knowing what the errors are! If you are worried that the errors are too large then put them in a txt document and attach them or something...
Make sure that you have the basics for compiling.. ```
sudo aptitude install build-essential
```

---

### Post by Mydrid on 2007-02-11
OK. I have duly attached a txt file (errors.txt) with the steps I take and the errors i get. The errors take up too much space to put them up directly on the board. I am getting all of the errors at the stage where I use the 'make' comand in the ndiswriter souce folder. Thanks for the help. Massively appreciated.

---

### Post by pay on 2007-02-11
> Make sure there is a link to the kernel source from the modules directory.Try to link the kernel source (/usr/src/linux) instead of the headers, (I might be horribly wrong about this though) ie ```
sudo ln -s /usr/src/linux /lib/modules/2.6.17-10-generic/build
```Even though ndiswrapper should already be working in Ubuntu (from what I've read, I've never actually used it).

Also alsa can be compiled into the kernel or as a separate package. I think (but have no proof) that the Ubuntu kernel has it compiled into the kernel opposed to the latter. Someone else might know what the real case is (I use Gentoo, not Ubuntu).

Also where are the errors you're getting from the alsa card?

---

### Post by Mydrid on 2007-02-11
> **pay said:**
> 
Make sure that you have the basics for compiling.. ```
sudo aptitude install build-essential
```

This is what I get when I use that command:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

As for the ALSA Errors, maybe I shoul  sort that out once I get the internet working with ndiswrapper, as I am currently having to shut down / reboot between Windows and Ubuntu to get this information. I can't figure out how to leave a CD-R 'open' after writing files, so I have now used two CD-Rs with less than 1mb on each to transfer data between linux / windows to post on here. Thanks again for all the help. 

I already have ALSA on the system... I am just trying to install the 1.0.14rc2 driver that will hopefully support my EMU 1820m soundcard... Hopefully!

---

### Post by Mydrid on 2007-02-11
In this forum thread, there is an issue with the exact same wireless adapter that I have. He says that it works fine with Dapper. Should I just install dapper instead? [http://ubuntuforums.org/showthread.php?p=1891889](http://ubuntuforums.org/showthread.php?p=1891889)

---

### Post by pay on 2007-02-11
Have you looked at [this](http://www.ubuntuforums.org/showthread.php?t=225206) found in the link that you provided?

---

