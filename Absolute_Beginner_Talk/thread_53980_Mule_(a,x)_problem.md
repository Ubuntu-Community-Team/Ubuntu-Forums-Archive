---
title: "Mule (a,x) problem"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by Buran on 2005-08-02
I`m would like to open , previosly worked , aMule, but geting this instead :

[QUOTE...]amule
Initialising aMule
Checking if there is an instance already running...

--------------------------------------------------------------------------------A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------Current version is: aMule 2.0.3 using wxGTK2 v2.5.3 (Unicoded)
Running on: Linux 2.6.10-5-386 i686

[2] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.5.so.3[0xb7a5d5e8]
[3] ?? in [0xffffe420]
[4] wxBitmapButtonBase::SetLabel(wxString const&) in amule [0x81a99dc]
[5] wxListItem::wxListItem(wxListItem const&) in amule [0x8167535]
[6] wxSpinEvent::GetClassInfo() const in amule [0x82363c6]
[7] wxAppBase::SetPrintMode(int) in amule [0x807adc1]
[8] wxAppBase::SetPrintMode(int) in amule [0x8077bbf]
[9] wxAppBase::SetPrintMode(int) in amule [0x8077d39]
[10] ?? in amule [0x806bd58]
[11] wxAppBase::SetPrintMode(int) in amule [0x8077f0f]
[12] wxAppConsole::CallOnInit() in amule[0x8074ec1]
[13] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.5.so.3[0xb79eda45]
[14] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.5.so.3[0xb79edb2d]
[15] wxAppBase::SetPrintMode(int) in amule [0x80776db]
[16] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb77358c8]
[17] wxMemoryDC::SetPen(wxPen const&) in amule[0x80647a1][/QUOTE]

what i should do in order to fix the problem. ](*,) 

P,S, xMule close itself every time i start it.May be there is some other program (stable) that mey halp me working in Donkey/Mule network ?

---

### Post by ubuntu_demon on 2005-08-03
IMO aMule is the best donkey client. But bittorrent is so much faster than amule. You should check it out.

How did you install aMule ?
the proper way to install amule is  (without the $) :
$ sudo apt-get install amule

---

### Post by KingBahamut on 2005-08-03
apt-get install gtk-gnutella azureus 
=) 

Solves both problems.

---

### Post by ubuntu_demon on 2005-08-03
azureus is a nice bittorrent client. But IMO the fastest bittorrent client which is userfriendly is gnome bittorrent (don't type the $) :
$ sudo apt-get install gnome-btdownload

---

### Post by KingBahamut on 2005-08-03
[QUOTE=ubuntu_demon]azureus is a nice bittorrent client. But IMO the fastest bittorrent client which is userfriendly is gnome bittorrent (don't type the $) :
$ sudo apt-get install gnome-btdownload[/QUOTE]
 Touche Demon. 
=)

---

### Post by ubuntu_demon on 2005-08-03
[QUOTE=KingBahamut]Touche Demon. 
=)[/QUOTE]
 :-P
hey I use azureus myself .. but I have learned not to advise it to average users :)

---

### Post by KingBahamut on 2005-08-03
[QUOTE=ubuntu_demon]:-P
hey I use azureus myself .. but I have learned not to advise it to average users :)[/QUOTE]
 Purely Admireable.

---

### Post by Buran on 2005-08-03
[QUOTE=ubuntu_demon]IMO aMule is the best donkey client. But bittorrent is so much faster than amule. You should check it out.

How did you install aMule ?
the proper way to install amule is  (without the $) :
$ sudo apt-get install amule[/QUOTE]

I did the apt-get thing etc.
My Azureus Bittorrent client also sends me out :
> /usr/bin/azureus: line 2: /usr/share/java-config/libswt-3.1-java: No such file or directory

---

### Post by Buran on 2005-08-03
Downloaded the Gnutella client ' thanks to KingBahamut.
I`ll try this network, but still would like to use the eMule and Bittorrent network as well...

---

### Post by ubuntu_demon on 2005-08-03
[QUOTE=Buran]I did the apt-get thing etc.
My Azureus Bittorrent client also sends me out :[/QUOTE]
 did you install azureus using apt-get ?

---

### Post by ubuntu_demon on 2005-08-03
[QUOTE=Buran]Downloaded the Gnutella client ' thanks to KingBahamut.
I`ll try this network, but still would like to use the eMule and Bittorrent network as well...[/QUOTE]
 like I said before : 
azureus is a nice bittorrent client. But IMO the fastest bittorrent client which is userfriendly is gnome bittorrent (don't type the $) :
$ sudo apt-get install gnome-btdownload

like I asked before :
How did you install aMule ? You should install it using apt-get

---

### Post by Buran on 2005-08-03
Yes I did istalled aMule & Azureus by apt-get.
P.S. gnome-btdownload is good , working and simple.

---

### Post by KingBahamut on 2005-08-03
[QUOTE=ubuntu_demon]did you install azureus using apt-get ?[/QUOTE]
 no problem Buran, gtk-gnutella is just easier to deal with IMHO.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=Buran]Yes I did istalled aMule & Azureus by apt-get.
P.S. gnome-btdownload is good , working and simple.[/QUOTE]
 what does your sources.list look like ?
Do you have backports and extras enabled (and not the staging ones) ?

---

### Post by Buran on 2005-08-05
How can i check this things ?

---

### Post by KingBahamut on 2005-08-05
[QUOTE=Buran]How can i check this things ?[/QUOTE]
 Applications -> Run Application -> xterm -> 

cd /etc/apt
sudo nano sources.list 
<supply  nessecary password>
edit file to your content. I typically remove the CDROM entry, and uncomment the nessecary fields. Also will need to add the backports if you dont have them. [http://ubuntuguide.org](http://ubuntuguide.org) for more information there. 

Ctrl-X , Y to save, Enter to save as sources.list. 

Then 

apt-get update

Reverify.

---

### Post by Buran on 2005-08-09
After doing this :
> cd /etc/apt
sudo nano sources.list
<supply nessecary password>

I have got an empty list in the xterm , whithout any items.

The backports are fine, i think, because when i`m trying to do the > apt-get install amule  thing , i see it is nothin to update...

Like this > # apt-get install amule
Reading package lists... Done
Building dependency tree... Done
amule is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Stiil can`t use the Mule network  ](*,)

---

### Post by ubuntu_demon on 2005-08-09
[QUOTE=Buran]After doing this :

```

cd /etc/apt
sudo nano sources.list
<supply nessecary password> 

```

I have got an empty list in the xterm , whithout any items.

[/QUOTE]
you probably mistyped. you should see the contents of your sources.list if you type :
$ cat /etc/apt/sources.list

please follow the ubuntuguide and change your sources.list

---

### Post by Buran on 2005-08-09
Ok , this is what I get :
> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main r estricted


deb [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multive rse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse  restricted

Am I in a  good state ?

---

### Post by ubuntu_demon on 2005-08-09
[QUOTE=Buran]Ok , this is what I get :


Am I in a  good state ?[/QUOTE]
 yeah you are !

---

### Post by ubuntu_demon on 2005-08-09
maybe this will solve your amule problem ... try :
$ sudo apt-get install libwxgtk2.5.3

---

### Post by Buran on 2005-08-09
So what is my problem ?! ](*,)

---

### Post by ubuntu_demon on 2005-08-09
[QUOTE=Buran]So what is my problem ?! ](*,)[/QUOTE]
 I think it's something with libwxgtk 
did you try my suggestion ?

---

### Post by Buran on 2005-08-11
> ~$ sudo apt-get install libwxgtk2.5.3
Password:
Reading package lists... Done
Building dependency tree... Done
libwxgtk2.5.3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 ](*,)

---

### Post by ubuntu_demon on 2005-08-11
[QUOTE=Buran]](*,)[/QUOTE]

well just use bittorrent since amule isn't worth your troubles IMO

otherwise try searching for some error messages with google or on the forums

---

### Post by KingBahamut on 2005-08-11
Demon....tried to convince him of gtk-gnutella.....but as usual Im typically wrong.

---

### Post by KingBahamut on 2005-08-11
Is it just me or is the smiley banging into the wall somewhat slightly annoying? 

Its just me, I know it.

---

### Post by ubuntu_demon on 2005-08-12
[QUOTE=KingBahamut]Demon....tried to convince him of gtk-gnutella.....but as usual Im typically wrong.[/QUOTE]
 everyone has their own preferred applications :)
I didn't mean any disrespect.

---

### Post by KingBahamut on 2005-08-12
Nah, im the Token Scottish guy in my area.....others live to kick me in the ribs......=)

---

### Post by Buran on 2005-08-13
King Bahamut , 
I didn`t mean to annoy you.
All that was in my intention is to find help  using Mule network.

---

### Post by ubuntu_demon on 2005-08-13
[QUOTE=Buran]King Bahamut , 
I didn`t mean to annoy you.
All that was in my intention is to find help  using Mule network.[/QUOTE]
 you didn't annoy him. he's a cool guy :)

search the forums for more on amule. I'm out of ideas.

---

