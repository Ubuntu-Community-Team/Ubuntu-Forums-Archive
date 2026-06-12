---
title: "Cannot swap boot order - Emac"
date: 2011-02-03
forum: Apple Hardware Users
---

### Post by sunnyd47 on 2011-02-03
With my ubuntu iso in the dvd drive, I do not get any boot from options for it to be used as boot drive within the boot order from the boot control panel. On startup with the alt key pressed I only get the Mac drive but when I change the boot to the other option (network) and press the alt key on startup, I get the boot order screen with the Mac HD and also the Ubuntu iso but cannot get the Ubuntu to highlight and use, just the Mac remains highlighted. On the same screen I get a very small wrist watch to the left of the screen that the mouse can move up and down but not to the side.

I am using a windows usb keyboard and usb mouse, I have used all manner of keyboard combinations to get the Ubuntu disc to highlight but nothing seems to work.

Within the drive section, the "My Mac" drive is locked and cannot partition it or change anything about it.

Has anyone any ideas that I can try? I did not want to get a Mac keyboard and Mouse as yet seeing as I wish to change the operating system to ubuntu.

---

### Post by linuxopjemac on 2011-02-03
try booting with the "c" key pressed

---

### Post by sunnyd47 on 2011-02-03
> **linuxopjemac said:**
> try booting with the "c" key pressed

Tried this many times, all that happens is the DVD drawer opens and the computer boots into Mac as normal.

As said, I can get the Ubuntu iso to register at boot alongside the Mac (with the windows Alt key) but cannot use the mouse nor keyboard to select the ubuntu iso to boot from it.

In system preferences there is no option to boot from the dvd, just Mac and Network startup. The "MyMac" drive is locked, is there a way (without orignal cds as bought second hand without them) to unlock or partition it which would at least (possibly) help me install Ubuntu.

---

### Post by linuxopjemac on 2011-02-03
try to boot from open firmware:
```
boot cd:,\\:tbxi
```

see [http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

---

### Post by sunnyd47 on 2011-02-03
> **linuxopjemac said:**
> try to boot from open firmware:
```
boot cd:,\\:tbxi
```see [http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

Yep, I did this and with a bright orange/red background Ubuntu 9.04 ppc went through its setup. BUT, when it rebooted, it goes through a screen stating you can type help and then goes to another screen (grey) which ends with returning from "prom innit" and then to a black screen which states "Loading.....". That closes and goes to a black screen with a still white "_" top left of screen, the "_" disappears and then I get the Ubuntu "drum roll" and nothing else, just a black screen.

I have used "Linux nosplash" and it loads all of the info with (ok) against all items but then goes to black screen and then get the drumroll. Tried "Linux nosplash video=ofonly" also, same result as above.

Ubuntu is obviously on the computer, does the drumroll being sounded mean that the issue is simply a screen display issue?

I have still been able to open open firmware and have tried to use the "boot tbxi" command again but it will not enter, just sits there.

(as an aside, to make my windows keyboard do a backslash on the mac I used the # (hash) key).

---

### Post by linuxopjemac on 2011-02-04
your xorg.conf file is missing, what is the exact emac? give me a link in everymac.com pls

---

### Post by sunnyd47 on 2011-02-04
> **linuxopjemac said:**
> your xorg.conf file is missing, what is the exact emac? give me a link in everymac.com pls



It is an Emac G4/700 [http://www.everymac.com/systems/apple/emac/stats/emac_700.html](http://www.everymac.com/systems/apple/emac/stats/emac_700.html)

Model No= A1002

EMC= 1903

Number  = Emac 700/512/48G/combo/S

Serial UM3100TCNU2

---

### Post by linuxopjemac on 2011-02-04
at the boot prompt in yaboot type:
```
Linux 1
```
you will boot into single user mode
then login with root password, then:
```
wget http://mac.linux.be/files/xorg/emac6.txt
mv emac6.txt /etc/X11/xorg.conf
```
CTRL-D to resume booting

---

### Post by sunnyd47 on 2011-02-04
> **linuxopjemac said:**
> at the boot prompt in yaboot type:
```
Linux 1
```
you will boot into single user mode
then login with root password, then:
```
wget http://mac.linux.be/files/xorg/emac6.txt
mv emac6.txt /etc/X11/xorg.conf
```
CTRL-D to resume booting

As soon as I type in and enter "Linux 1", it continues to boot as described, "Loading..." and then black screen with the ubuntu drum roll. No options for adding the second code you gave.

---

### Post by linuxopjemac on 2011-02-04
What about 
```
Linux 1 nosplash
```

---

### Post by sunnyd47 on 2011-02-04
> **linuxopjemac said:**
> What about 
```
Linux 1 nosplash
```

The same result, checks through with OK next to all items and then screen stays black and then get the drum roll.

Also, as said I am using a windows keyboard and am trying another fix recommended, the trouble is it requires a ~ and from my keyboard cannot find where to replicate it. From the norm windows alt+~ I get similar to "l". Even the name of this ~ could help my search should someone know it.

---

### Post by linuxopjemac on 2011-02-04
Cannot you get into a tty from the black screen with CTRL-Alt-Fx (Fx=F1-F6)?

If nothing works, I recommend MintPPC.

---

### Post by sunnyd47 on 2011-02-04
> **linuxopjemac said:**
> Cannot you get into a tty from the black screen with CTRL-Alt-Fx (Fx=F1-F6)?

If nothing works, I recommend MintPPC.

Yes, can get to the tty4 screen ok, what should I type in there? I have tried the following and am not sure if it is the correct script, nothing works except stopping it and starting it again, the 2nd and third are not .

user@ubuntu ~# sudo service gdm stop
 followed by


  user@ubuntu ~# sudo Xorg -configure (when tried states sudo: xorg: command not found)

followed by

user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf (when tried states mv: missing destination file etc)

 followed by


 user@ubuntu ~# sudo service gdm start


I have also tried 
sudo gedit /etc/XLL/xorg.conf

but this comes back as "(gedit:3756): gtk-Warning **:cannot open display"

---

### Post by sunnyd47 on 2011-02-05
I am now (after many tries) at the screen which says "Ubuntu is in low graphics mode" and it then gives me options. I have changes the monitor settings to

Identifier general monitor
option   DPMS

HorizSync   71-73

VertRefrsh   70-140

but still its in low graphics mode. Are these sttings above OK and are there other settings to chabge within the same config screen?

---

### Post by linuxopjemac on 2011-02-05
if you are in a tty you have to download the working xorg.conf file for your emac. First login as root.
```
su
wget http://mac.linux.be/files/xorg/emac6.txt
mv emac6.txt /etc/X11/xorg.conf
/etc/init.d/gdm restart
```
if that does not work, reboot.

---

### Post by sunnyd47 on 2011-02-05
> **linuxopjemac said:**
> if you are in a tty you have to download the working xorg.conf file for your emac. First login as root.
```
su
wget http://mac.linux.be/files/xorg/emac6.txt
mv emac6.txt /etc/X11/xorg.conf
/etc/init.d/gdm restart
```
if that does not work, reboot.

Downloaded the file OK and saved.

The second line of input code result states
mv: try to overwrite'/etc/X11/xorg.conf', overriding node 0644 (rw-r--r--)? I placed in "rw" and then entered but nothing happens on screen just get another fresh line start, is this right? I tried with a Y for ys and it folowed with Permission denied. Am I not logged in as root?

Taking into account the above, the third line of code input, the result states
stopping GNOME display manager.....     (OK)
starting GNOME display manager.....      (fail)

---

### Post by sunnyd47 on 2011-02-05
HEY, whatever I did right or wrong, now I have brand new shiny UBUNTU 9.04 on my redundent old Emac.

Thanks so much linuxopjemac for your help and patience, you are a star and no mistake!!:KS

---

### Post by linuxopjemac on 2011-02-05
you have to login as root I guess with
```
su
```
and then give your root password before you can move that file.

I don't know how Ubuntu handles root stuff nowadays. If you have sudo installed you might want to do it as normal user using sudo.

---

### Post by sunnyd47 on 2011-02-05
> **linuxopjemac said:**
> you have to login as root I guess with
```
su
```
and then give your root password before you can move that file.

I don't know how Ubuntu handles root stuff nowadays. If you have sudo installed you might want to do it as normal user using sudo.

Thanks agin.

Now, in update manager it says that 9.10 is available, should I do it or leave well alone for now? I assume that it will update to 9.10 ppc ;-)

---

### Post by linuxopjemac on 2011-02-05
that I would not do. If you want to install Karmic Koala, you better install from scratch. But why didn't you install 10.04 ? It's a LTS version which will have updates until April 2015.

---

### Post by sunnyd47 on 2011-02-05
> **linuxopjemac said:**
> that I would not do. If you want to install Karmic Koala, you better install from scratch. But why didn't you install 10.04 ? It's a LTS version which will have updates until April 2015.

Mistakenly I read somewhere that the support for xorg was builtinto 9.o4, my mistake.
So, if I choose to install 10.04 afresh now, will I have the same trouble with the xorg with the ppc version?

---

### Post by linuxopjemac on 2011-02-05
I am sure you will, but you just have to repeat the steps you did for 9.04. Wget the xorg.conf file and move it. That's it. If you don't care about LTS (if yyou like installing), you might want to opt for 10.10.

On another note, don't you think GNOME is too slow on that machine? I would install the lubuntu-desktop.

---

### Post by sunnyd47 on 2011-02-05
Would you recomend a particular release of Lubuntu? I have looked briefly and am unsure with that system. Are they LTS or just for ppc? Do they use xorg also?
Would I have to remove gnome in a special way or will Lubuntu just install from boot CD correctly?

Currently my Vaio desktop has Ubuntu 10.10 and I really like it, did have vista but it got me frustrated for many reasons. If I got the Ubuntu LTS on this old Mac, that would be cool too.

---

### Post by linuxopjemac on 2011-02-06
I would just install Ubuntu 10.04 and from there I would install Lubuntu. Just do as you did for 9.04. If you have X working and you are in a GNOME sesstion you issue the following command:
```
sudo apt-get install lubuntu-desktop
```
If it is installed, logout and choose LXDE as session instead of Gnome. You are in Lubuntu then.

If you feel like experimenting, you can also try MintPPC and see which you like better, Lubuntu or MintPPC.

---

### Post by sunnyd47 on 2011-02-06
> **linuxopjemac said:**
> I would just install Ubuntu 10.04 and from there I would install Lubuntu.

I am trying to install 10.04 but now, from the burnt iso I get to yaboot screen, it says states that it is with 10.04 and then Kernel etc and then goes to a black screen, unlike before, I do not get a drum roll. The above is with the command boot "c". I have tried the tbxi command with no joy, gets to prom-ennit (or whatever it flashes), goes to black screen with curser top left and then goes to plain black screen and nothing else happens, no drum roll.

Do I need to remove my 9.04 in some way or do anything else to allow 10.04 to install over it?

---

### Post by linuxopjemac on 2011-02-07
can you boot with
```
video=ofonly nosplash
```
as kernel argument ?

---

### Post by sunnyd47 on 2011-02-07
> **linuxopjemac said:**
> can you boot with
```
video=ofonly nosplash
```as kernel argument ?

No, it will not do it.

I get the bootstrap screen, booting from cd is chosen.

Goes to the Lucid Lynx yaboot screen, I enter help and then tab, all options then shown are for "live", with *live being the main one and all have - and not an = sign for other permutations asn in video-ofonly. None of these options make it boot, just goes to the blackscreen (the cd is running though) and no drum roll.

---

### Post by linuxopjemac on 2011-02-07
use the alternate installer then, not the live CD:
[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)

see [http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/)

---

### Post by sunnyd47 on 2011-02-10
I have tried the alternate cd with no joy also, briefly I get the 10.4 screen with the dots but that flashes of very quickly and nothing else happens (black screen). 

I also tried debian, as instructed by the install pages. I managed to get debian loaded OK but the instructions for actually getting mint installed after did not work. I managed to download mint and it was saved, the second instruction failed.

Maybe I should just put it in the skip, seems a shame though as the machine is still trying to give things a go.

---

### Post by linuxopjemac on 2011-02-10
why did mintppc fail and why didn't you report it in the forums ?

---

### Post by sunnyd47 on 2011-02-10
> **linuxopjemac said:**
> why did mintppc fail and why didn't you report it in the forums ?

wget [http://mintppc.org/files/mintppc9/mint-installer](http://mintppc.org/files/mintppc9/mint-installer)
downloaded OK
[FONT=Verdana]
[/FONT]This line 
chmod +x mint-installer

did nothing, tried it four or five times.

---

### Post by linuxopjemac on 2011-02-11
nothing "happens". I mean you don't see anything happening, but that command works. Then you need to continue with the rest of the installation steps....

---

### Post by sunnyd47 on 2011-02-11
> **linuxopjemac said:**
> nothing "happens". I mean you don't see anything happening, but that command works. Then you need to continue with the rest of the installation steps....

I will give it another go, thanks for your patience.

---

### Post by sunnyd47 on 2011-02-11
> **linuxopjemac said:**
> nothing "happens". I mean you don't see anything happening, but that command works. Then you need to continue with the rest of the installation steps....

So, I am at it again :-)

Debian loaded OK. 

downloaded mint-installer OK

typed "chmod +x mint-installer" and hit enter, nothing happens physically just goes to another command line where I typed "sudo passwd" (I assume this is my password that I created on install and not the word "passwd")  and get "-bash: sudo: command not found"

---

### Post by linuxopjemac on 2011-02-11
my fault, I changed the instructions:
```
su
```
give your root password, install sudo
```
apt-get install sudo
```
continue with the installation instructions

---

### Post by sunnyd47 on 2011-02-11
> **linuxopjemac said:**
> my fault, I changed the instructions:
```
su
```give your root password, install sudo
```
apt-get install sudo
```continue with the installation instructions

I have tried su with my password and that states "unknown id:"
I only use one so I know it is what was added on debian install.

---

### Post by linuxopjemac on 2011-02-11
you don't have a root (administrator) password ???

---

### Post by sunnyd47 on 2011-02-11
> **linuxopjemac said:**
> you don't have a root (administrator) password ???

All I have done is install debian, with passwords and user details. What root password do I need or where do I get it from? If it is from my old Mac, all passwords were the same as I have used in debian.

I am more confused than ever.

---

### Post by linuxopjemac on 2011-02-11
Normally you have to give a password for the root account during installation of Debian. This also counts for other distributions like Ubuntu. Maybe you did not set a root password during installation yet. In that case you have to set it now, as was written in the installation instructions. To do that:

```
sudo passwd
```
and then you give the desired password for root.

Then login as root:
```
su
```
then you give that same root password and you install sudo as per the instructions. Hope this helps.

---

### Post by sunnyd47 on 2011-02-11
> **linuxopjemac said:**
> Normally you have to give a password for the root account during installation of Debian. This also counts for other distributions like Ubuntu. Maybe you did not set a root password during installation yet. In that case you have to set it now, as was written in the installation instructions. To do that:

```
sudo passwd
```and then you give the desired password for root.

Then login as root:
```
su
```then you give that same root password and you install sudo as per the instructions. Hope this helps.

But I have done all of this. Given all passwords into debian on install when asked, it should accept it.

If I add "sudo (and my set debian password), I get "-bash: sudo: command not found"
If I add su (and my set debian password), I get "unknown id: (my debian password)
 
If I add sudo passwd, I get "unknown id: passwd"
If I add su passwd, I get "unknown id: passwd"

Are the debian passwords stored within the same partition as debian itself? i wondered if the partitions are fudged in some way and they cannot connect? probably way off here but just trying to think of a reason why the passwords either cannot be found of have not been stored.

---

### Post by linuxopjemac on 2011-02-11
omg
it's:
```
su
```
then you press enter, then you give your root password....

---

### Post by sunnyd47 on 2011-02-11
> **linuxopjemac said:**
> omg
it's:
```
su
```then you press enter, then you give your root password....


Never mind the OMG, if the instructions arent clear, they arent clear. I am obviously trying to follow current installation information that is online that needs to be changed. 

If it had said from the start, type "su" hit enter and then add password I would have done and could have saved myself a lot of trouble and time.

---

### Post by linuxopjemac on 2011-02-12
From now on please post your problems in the mintppc forums. For that you need to register:
[http://www.mintppc.org/forums/ucp.php?mode=register](http://www.mintppc.org/forums/ucp.php?mode=register)

I will adapt the instructions a little.

---

### Post by sunnyd47 on 2011-02-12
> **linuxopjemac said:**
> From now on please post your problems in the mintppc forums. For that you need to register:
[http://www.mintppc.org/forums/ucp.php?mode=register](http://www.mintppc.org/forums/ucp.php?mode=register)


I will be doing so, thanks

---

### Post by linuxopjemac on 2011-02-12
Can you have a look if the installation instructions are clearer right now ? If you have any remarks please let me know.

---

