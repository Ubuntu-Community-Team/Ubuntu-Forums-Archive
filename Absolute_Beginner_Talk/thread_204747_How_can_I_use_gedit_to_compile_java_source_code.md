---
title: "How can I use gedit to compile java source code"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by pigmario on 2006-06-27
In Windows world, I use editplus to create compile Tools and run Tools, to compile and run java but in Linux world are there any program that can do the function like editplus, I don't need program that auto fill syntax for me because I just start learning java and I also figure out that gedit has plugin name external tool to run command on terminal but I don't know how to put command look like > javac filename.java  to program, So I want to what command to put on external tool to make gedit work or are there any program that do the job and how?.
 Any suggestion would be appreciate. :)

---

### Post by FuturePast on 2006-06-27
I think it would be "javac $GEDIT_CURRENT_DOCUMENT_URI"

---

### Post by pigmario on 2006-06-27
Thanks for reply
             I found that to use > $GEDIT_CURRENT_DOCUMENT_NAME as environment variable to make Compile command run but I can't found environment variable for Run command wich use only filename with no extension.
Any suggestion?
Or I have to ask programmer who make External Tool to make new environment variable?

---

### Post by FuturePast on 2006-06-28
Yes, I think you would have to make a feature request for this.

---

### Post by stupidkid on 2006-06-28
If you're a hardcore Java programmer, you can try eclipse. It's a powerful Java IDE.

---

### Post by derby007 on 2006-06-29
Can i ask a Q, related to above: if i'm not connected to the internet (ie. my Ubuntu installation is not connected), is there a way to get these packages eg. Anjuta or other IDE's for Java, without too much hassle... :rolleyes:

---

### Post by stupidkid on 2006-06-29
[QUOTE=derby007]Can i ask a Q, related to above: if i'm not connected to the internet (ie. my Ubuntu installation is not connected), is there a way to get these packages eg. Anjuta or other IDE's for Java, without too much hassle... :rolleyes:[/QUOTE]
I don't think so...But why aren't you connected to the internet?

---

### Post by derby007 on 2006-06-30
[FONT="Book Antiqua"]I cant get broadband on that PC at home, and i'm not paying a fortune for 56K slooow internet connection. So i'll wait for Broadband to call to my area, until then i have to download .deb files & transport them to my Ubuntu PC. :( [/FONT]

---

### Post by stupidkid on 2006-06-30
Yea, that's what I was gonna suggest too. But programs always require so many different dependencies and so that might cause some hassel.

---

### Post by hotbrainz on 2006-06-30
hey derby 007, it is possible to get eclipse on your system without internet. There are 2 ways:

1.download the linux version from the eclipse site - extract it and its ready to use. 
2.download the eclipse package from [http://package.ubuntu.com](http://package.ubuntu.com) and installing it [http://packages.ubuntu.com/dapper/devel/]("http://packages.ubuntu.com/dapper/devel/")

I recommend the  **option 1**    coz i got it runing right away, no problems at all.

All said and done, there may be issues with plugins ( you can probably get them after you have broadband ) but the basic java should be no problems.

Good luck

---

### Post by crystal on 2006-06-30
> hey derby 007, it is possible to get eclipse on your system without internet. There are 2 ways:

1.download the linux version from the eclipse site - extract it and its ready to use.
2.download the eclipse package from [http://package.ubuntu.com](http://package.ubuntu.com) and installing it [http://packages.ubuntu.com/dapper/devel/](http://packages.ubuntu.com/dapper/devel/)
But how would one download without an Internet connection?

---

### Post by hotbrainz on 2006-06-30
hey Crystal, 

There is no connection to the Ubuntu box, but you can always download from a cyber cafe if not from office. Then take the package home in a USB or CD :). Then install. Well am I missing something here?

---

### Post by crystal on 2006-06-30
> There is no connection to the Ubuntu box, but you can always download from a cyber cafe if not from office.
Oh, I get it now. It did seem strange at first to download without an Internet connection :)

---

### Post by hotbrainz on 2006-06-30
Happy to help :)

---

### Post by derby007 on 2006-06-30
[FONT="Comic Sans MS"]=D> Cheers, i have been doing this, ie. installing .deb files. Its a pity about no internet connection on Ubuntu PC but i enjoy the challenges. It tells me more about the OS. I'm new to Linux & Ubuntu OS & its brill, eg. just downloaded BMP player for MP3's, i only now see how MSWindows has a stranglehold on the PC world, pity. 8-) [/FONT]

---

### Post by stinkinrich88 on 2007-05-06
nooo, there is a way to do it! I've done it before! It's some werid code to remove the file extension like '$GEDIT_CURRENT_DOCUMENT_NAME/\.jpg$//’  or something, but I can't figure it out

any ideas? Wish I had saved it somewhere before i installed ubuntu

---

### Post by stinkinrich88 on 2007-05-06
> **stinkinrich88 said:**
> nooo, there is a way to do it! I've done it before! It's some werid code to remove the file extension like '$GEDIT_CURRENT_DOCUMENT_NAME/\.jpg$//’  or something, but I can't figure it out

any ideas? Wish I had saved it somewhere before i installed ubuntu


Oh dear, so close, if anyone is interested, this is how you loose the file extension:

${GEDIT_CURRENT_DOCUMENT_NAME%\.*} 

so this is how you run java applications in gedit:

java ${GEDIT_CURRENT_DOCUMENT_NAME%\.*}

---

