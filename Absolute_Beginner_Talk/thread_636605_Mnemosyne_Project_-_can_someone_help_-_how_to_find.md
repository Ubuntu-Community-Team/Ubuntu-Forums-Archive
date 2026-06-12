---
title: "Mnemosyne Project - can someone help - how to find &amp; install more cards."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-10
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Mnemosyne](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Mnemosyne)

>  How to install Mnemosyne

Mnemosyne is a sophisticated free flash-card tool which optimizes your learning process. To install the latest version in the repositories run the following command

sudo apt-get install mnemosyne

or use Synaptic Package Manager under System => Administration menu, to locate and install the mnemosyne package.

To install the latest version (the one in the repository is somewhat out of date) first install the dependencies:

sudo apt-get install python python-pygame python-qt3 python-support python-xml

then download the latest source package from here:

wget [http://superb-east.dl.sourceforge.net/sourceforge/mnemosyne-proj/mnemosyne-0.9.10.tgz](http://superb-east.dl.sourceforge.net/sourceforge/mnemosyne-proj/mnemosyne-0.9.10.tgz)
(correct as of 11 Nov 2007)

Decompress it:

tar -xzf mnemosyne-0.9.10.tgz

go to the directory

cd mnemosyne-0.9.10/

run this command to install it:

sudo python setup.py install

To create a launcher for it in your Applications Menu:

System => Preferences => Main Menu => Education (or wherever) => New Item:
Name: Mnemosyne
Command: mnemosyne


**I couldn't manage the end bit with putting a launcher in the Education drop down menu**

yes i did remove the* "(or wherever)"*

so please how to do it?
===================

from here i installed the Latic Voc cards** (Wheelock_Latin.zip)**
[http://sourceforge.net/project/showfiles.php?group_id=159201&package_id=229650](http://sourceforge.net/project/showfiles.php?group_id=159201&package_id=229650)

>  	Wheelock Latin Notes (2007-10-30 01:26)
  	Wheelock_Latin.zip  Mirror 	19123 	309 	Platform-Independent 	Source .zip
  	chinese-hsk Notes (2007-10-12 11:04)
  	chinese-hsk-1.1.zip  Mirror 	488862 	78 	Any 	Source .zip
  	medicine Notes (2007-09-22 00:08)
  	medicine-20071103.zip  Mirror 	53650 	62 	Platform-Independent 	Source .zip
  	basic_chinese Notes (2007-04-24 07:28)
  	Basic_Chinese.zip  

did also get **Basic_Chinese.zip**, but i dunno how to make it work.

thanks for any help, or if you know better apps for learning languages.

---

### Post by antisocialist on 2007-12-10
rosettastone is better i think, but its
1 not for linux
2 for windoze
3 not open source
4 not free

---

### Post by MozartlovesUbun2 on 2007-12-10
> **antisocialist said:**
> rosettastone is better i think, but its
1 not for linux
2 for windoze
3 not open source
4 not free

ok

but i like this flash card system, basically can be used for anything you wanna learn, as with most of the free apps it's not very polished though.

---

### Post by ptmkenny on 2008-04-15
The Mnemosyen Project recently released full documentation that is available here:
[http://www.mnemosyne-proj.org/help/index.php](http://www.mnemosyne-proj.org/help/index.php)

By the way, Rosetta Stone and Mnemosyne are nothing alike.  Rosetta Stone is for learning the basics of a foreign language.  Mnemosyne is a general memory aid for all sorts of knowledge.

---

### Post by berget on 2008-04-23
There's a very good article in today's Wired called ["Want to Remember Everything You'll Ever Learn? Surrender to This Algorithm"]("http://www.wired.com/medtech/health/magazine/16-05/ff_wozniak"). 

It doesn't mention any of the freeware open source alternatives to SuperMemo, but it sure started a new buzz about the fact that this method works, and it is currently the most popular article on Wired.

I've just started using MnemoSyne and I'm planning to put together some anatomy - musculoskeletal packages that I would gladly share.

I'm hoping the Mnemosyne Project gains some more popularity from this article as well!

---

### Post by BlondGirl on 2008-06-06
I've started making cards for studying sectional anatomy.  So far, I have general vocab and the bony skull, but I will get more eventually.  

I'd like to post these to the site--has anyone here done that yet?

---

### Post by BlondGirl on 2008-06-06
Ack!  Double post.

(Slinking away with my face red.)

---

### Post by krlhc8 on 2008-06-11
Mnemosyne is the coolest!  Attached is a file on linux commands from linuxguide.it.  Import as "text with tab separated Q/A"

---

### Post by krlhc8 on 2008-06-11
woops, here is the linux commands file attached...

---

### Post by OsakaWilson on 2008-06-26
Is it available in a file format that opens in Ubuntu? You see, until I learn the commands, the command line is not a part of Ubuntu as I know it. You have created a paradox!! :)

---

### Post by krlhc8 on 2008-06-26
Not sure I follow, but it does open in mnemosyne...  The file is now officicially supported on their website:

[http://www.mnemosyne-proj.org/category/2/15](http://www.mnemosyne-proj.org/category/2/15)

---

