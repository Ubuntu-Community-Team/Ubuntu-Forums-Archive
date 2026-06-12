---
title: "encyclopedia needed"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-08-31
i want an encyclopedia like britanica or something else. i searched in apt-cache but found no result. can anybody tell how can i find an encyclopedia .i believe that there would be many encyclopedias for linux but don't know why there isn't any in apt-cache. can anybody help me

---

### Post by amo-ej1 on 2006-08-31
Why do you want a software package to do that ? I think [http://www.wikipedia.org]("http://www.wikipedia.org") will do a much better job.

---

### Post by urukrama on 2006-08-31
I don't want to get into a debate here regarding Wikipedia, but because anyone can change it anytime, it isn't very reliable. I know several professors at my university who don't allow their students to rely on Wikipedia for their papers. Apart from that, it means you need an active internet connection to access it, which I don't always have.

I used Britannica 2002 on Windows XP. I tried it with Wine on Ubuntu Dapper. The installation went very smooth, but I can't actually start the program. I apparently need Java within Wine, but I haven't tried setting that up.

If there is an linux alternative, I'm all for it.

---

### Post by phido on 2006-08-31
Have a look at Stardict, you can install [various Dictionaries]("http://stardict.sourceforge.net/Dictionaries.php").
Dictionary looksup stuff on [dictd.org]("http://www.dict.org").

---

### Post by bruce89 on 2006-08-31
> **phido said:**
> 
Dictionary looksup stuff on [dictd.org]("http://www.dict.org").

You can use the dictionary applet in Applications>Accessories>Dictionary to lookup words from here too.

---

### Post by Anonii on 2006-08-31
> **urukrama said:**
> I don't want to get into a debate here regarding Wikipedia, but because anyone can change it anytime, it isn't very reliable. I know several professors at my university who don't allow their students to rely on Wikipedia for their papers. Apart from that, it means you need an active internet connection to access it, which I don't always have.

I used Britannica 2002 on Windows XP. I tried it with Wine on Ubuntu Dapper. The installation went very smooth, but I can't actually start the program. I apparently need Java within Wine, but I haven't tried setting that up.

If there is an linux alternative, I'm all for it.
Who needs real facts when you can make them up yourself, anyway?

---

### Post by urukrama on 2006-08-31
> **phido said:**
> Have a look at Stardict, you can install [various Dictionaries]("http://stardict.sourceforge.net/Dictionaries.php").
Dictionary looksup stuff on [dictd.org]("http://www.dict.org").

You just made my day! :KS I had been looking for something like this for a long time. Thank you, thank you, thank you. :D 

It looks very great. The only problem is I can't get it to run... If I click on the icon in the Applications menu, the program loads, but nothing actually comes up. (I have installed some dictionaries)

If I type 'stardict' in the terminal, this is what I get:

> stardict: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by stardict)


Is that something I have to install separately (couldn't find it in Synaptic) or does this indicate that something went wrong during the installation?

But when I type 'locate glibc' in the terminal, this is what I get:

> /etc/init.d/glibc.sh
/usr/share/aclocal/glibc2.m4
/usr/share/aclocal/glibc21.m4
/usr/lib/glib-2.0/include/glibconfig.h


Any suggestions?

---

### Post by u04f061 on 2006-08-31
oh  i am too much disappointed to learn that there isn't any encyclopedia for linux! stardict i tried is not efficient.moreover there is difference between dictionary and encyclopedia. i also don't need wikipedia because it requires active internet connection at all the time. plz guys think about it that there isn't any encyclopedia for linux. isn't it amazing????????? it is really harmful as well:^o

---

### Post by urukrama on 2006-08-31
u04f061, did you try out The Britannica Concise Encyclopedia for Stardict? It can be downloaded [here]("http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php").

---

### Post by u04f061 on 2006-09-01
> **urukrama said:**
> u04f061, did you try out The Britannica Concise Encyclopedia for Stardict? It can be downloaded [here]("http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php").


yes i have downloaded this but could not add it. i extracted the file and moved the file to /usr/share/stardict/dict but it was not added to it.so i can't use it. can u tell me how to add it plz.

---

### Post by T700 on 2006-09-01
I've not seen much interest or development in encyclopedias since the net became pervasive.  Yes, I understand that you don't have a net connection constantly, but honestly, what university level instructor is going to want to see a citation from an encyclopedia anyway?

Paul

---

### Post by urukrama on 2006-09-01
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=217931") thread on installing Stardict dictionaries? I haven't tried out Britannica yet, but all the others I installed work great!

---

### Post by urukrama on 2006-09-02
To those who had the same problem as I did (error message that glibc 2.4 is not found): following [this]("http://ubuntuforums.org/showthread.php?t=203364&highlight=glibc+2.4") thread I installed glibc 2.4 from the Edgy repos. All works fine now.

---

### Post by urukrama on 2006-09-03
> **urukrama said:**
> To those who had the same problem as I did (error message that glibc 2.4 is not found): following [this]("http://ubuntuforums.org/showthread.php?t=203364&highlight=glibc+2.4") thread I installed glibc 2.4 from the Edgy repos. All works fine now.

That was actually **not** such a good idea... ](*,)

Yes, Stardict works fine now, but it has resulted in some other difficulties. Some graphical elements don't display as they should (progress bars are entirely blank), though the system still works. Anytime I load a program from the terminal I get the following message:

> (leafpad [or whatever program I run]:6014): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(leafpad:6014): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",


In theory I should be able to downgrade, but I'm not able to do so. If, in Synaptic (through which I installed libc6) I try to force to use the dapper version, it tells me it will uninstall **everything** I have installed on my system. Following some advice on these forums I tried to "sudo aptitude install libc6", but that didn't do anything.

Those who think of doing something similar, read [these]("http://ubuntuforums.org/showthread.php?t=190349&highlight=libc+downgrade") [threads]("http://ubuntuforums.org/showthread.php?t=229087&highlight=libc+downgrade").

My system still runs fine (more or less), but I do want to revert back. Does anyone have any suggestions? Sorry for being a foolish noob. :wink:

EDIT: I found a solution (hurray!) in [this]("http://ubuntuforums.org/showpost.php?p=1153700&postcount=13") post. It seems to work. I think I'll be a bit more careful next time.

EDIT 2: All works fine if you install Stardict through Synaptic; don't use the website mentioned earlier.

---

