---
title: "Error when playing D"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by bubbadawg on 2006-02-19
Hello All ---

I just installed Ubuntu yesterday and am really like it. I decided to test out the DVD player and receive the following error when attempting to play a DVD:

```

The source seems encrypted, and can't be read. Are you trying to play an
 encrypted DVD without libdvdcss2?

```

I downloaded the libdvdcss thru apt-get and believe that it installed, but I still can't get it to play. I believe that I am using Totem to view the DVD.

Any help is greatly appreciated.

Thanks.

---

### Post by Jason_25 on 2006-02-19
I don't think it's possible to download through apt-get unless you are using non-ubuntu sources.  This is the official way from the wiki.  ```


sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh


```

---

### Post by bubbadawg on 2006-02-19
[QUOTE=Jason_25]I don't think it's possible to download through apt-get unless you are using non-ubuntu sources.  This is the official way from the wiki.  ```


sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh


```[/QUOTE]

Thanks, that did it! Since I just installed Ubuntu yesterday, I am new to the command line calls. Would you mind telling me what the second line does?  I am guessing that it is a command to install the file that was just downloaded, however, I am unsure of the last part - "install-css.sh"

Thanks for the kind assistance.

---

### Post by kingsidy on 2006-02-19
check this page it explains how to get libdvdcss2 and w32codecs

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/]("http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/")

---

### Post by Jason_25 on 2006-02-19
Your welcome.  

That last line runs a script that uses wget (I think) to download libdvd2css from a trusted website.  You can open up the script with a text editor to examine it yourself if you would like.

---

### Post by bubbadawg on 2006-02-19
[QUOTE=kingsidy]check this page it explains how to get libdvdcss2 and w32codecs

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/]("http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/")[/QUOTE]

Thanks.

Ok, I am totally new to Ubuntu and Linux and struggling to make my way thru it. I am following the instructions from the webpage you sent me to but I am stuck on:

[INDENT][I]Update: you can add the PLF repository to your sources.list to get the required multimedia codecs and binaries through apt-get (Synaptic).

The line to add to your /etc/apt/sources.list file would be:
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/I][/INDENT]

I attemtped to open the sources.list file in etc/apt/ using both the file explorer as well using terminal and am told that access is denied. How can I open this file?

Thanks and again I greatly appreciate all the help as I am new.

---

### Post by kingsidy on 2006-02-19
u need root privilege in order to edit the source list. at the terminal type in
> sudo gedit /etc/apt/sources.list

then you can add whatever repositories you want at the end of the file save. then do an apt-get update in order to refresh the package list.

---

