---
title: "absolute beginner - is there somewhere to go?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Keith65rider on 2008-03-11
Hi there,

I have installed 7.10 Ubuntu, 64 bit on myAMD PC.

Much to my delight, it all installed in 20 minutes, and I was on the internet, with it downloading updates. It all seems to work, internent, plays DVDs, copies CDs, games, etc. The free Office software is good, and Office spreadsheet can look at the new M$ Excel  sheet, that Office XP cannot do.

BUT, I cannot do anything with my Samsung SCX-4100 multi laser printer.

I have looked and downloaded drivers, but looking at the instructions, I get lost and baffled in the fiirst few lines.

Where do I type in sudo ./ etc (what is sudo?), or cups or the synaptic package manager?

Is there somewhere that explains it all that I can go to?

Cheers

KR

---

### Post by PmDematagoda on 2008-03-11
The commands are to be entered in the terminal which can be brought up through Applications>Accessories>Terminal.

You can find more information concerning sudo from [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by MONODA on 2008-03-11
ok first let me say that im happy that you like Ubuntu :).
When anyone tells you to "type" something, they mean to type it into what is called a "terminal" and press enter. The terminal is an application which lets you control your computer from a command line by entering what are called commands, like dos prompt in windows. You can open a terminal window by going apps->accessories-.terminal. I would configure the hotkeys in terminal so that paste is ctrl+v and copy is ctrl+c (it is ctrl+shift+v or ctrl+shift+c by default). sudo is a command that allows you to run another command as the administtrator also know as, root. CUPS is the Common Unix Printing System which allows you to print files. Synaptics package manager is a program which lets you manage all of the software on your system, known as packages. You can open Synaptic package manager from system->admin->synaptics package manager. A simpler version of synaptis which contains less packages is available via apps->add/remove.

---

### Post by bodhi.zazen on 2008-03-11
A new OS is overwhelming at first, that is what these forums are for. Feel free to ask any questions you have here and we will try to help.

I like this link :

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

Hope it helps :)

---

### Post by dstew on 2008-03-11
Did you get the drive package from the Samsung site? [Here]("http://www.samsung.com/us/support/download/supportDownDetail.do?group=printersmultifunction&type=printersmultifunction&subtype=monochromelasermultifunctionprintersfaxes&model_nm=SCX-4100&language=&cate_type=all&mType=DR&dType=D&vType=R&cttID=214860&prd_ia_cd=06010300&disp_nm=SCX-4100") is their driver package download page. The Ubuntu instructions at the bottom of the page are a little cryptic, even for someone who understands Ubuntu. Here is my recommendation. Do not log in as "root". That user is disabled in Ubuntu for security reasons. Do not enable the root account to install this driver.

1. Download the driver package to your desktop using the internet browser.
2. Double-click on the package file (has a .tar.gz at the end of its name) and extract the files to the desktop. You should see a cdroot folder on your desktop.
3. Open a terminal (just a plain old terminal. I don't know what they mean by "Root terminal")
4. Change your active directory to the cdroot folder on your desktop:```
cd ~/Desktop/cdroot
```
5. Make sure you are in the cdroot directory:```
ls -l
```The output should show the presence of the autorun script.
6. Execute the autorun script as a user with root privleges using sudo:```
sudo ./autorun
```
I got a whole wizard like configuration program at this point that will take you through the steps to install your printer driver. Now, if it works, please post back to the forum to let us know.

---

### Post by Keith65rider on 2008-03-12
Thanks for all the help - I am getting there slowly. I am still impressed how it can all install and do things in 20 minutes.

KR

---

