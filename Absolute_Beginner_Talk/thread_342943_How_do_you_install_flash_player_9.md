---
title: "How do you install flash player 9"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by bigmc on 2007-01-20
I am new to ubuntu and would like to know how to install flash player 9... I have no clue.. I downloaded the file... But what do I do now???

---

### Post by meng on 2007-01-20
Enable universe/multiverse repositories: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
then in the terminal:
sudo aptitude install flashplugin-nonfree

---

### Post by aysiu on 2007-01-20
If you do take that route, make sure you're using Edgy Eft (6.10) and have the Edgy backports repositories enabled.

Otherwise, these directions will work:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by highneko on 2007-01-20
Try "sudo apt-get install flashplugin-nonfree".

If it says the package can't be found or something then make sure you have the universe and multiverse sources uncommented in your "/etc/apt/sources.list" file. 

If you're gonna edit your sources.list file then you should back it up first like this "sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak".

---

### Post by bigmc on 2007-01-20
I tried that and got this:

Unable to lock the administration directory (/var/lib/dpkg), is another program using it?

and I do not know

Thanks for you help

---

### Post by aysiu on 2007-01-20
It's not enough to just have Universe and Multiverse enabled. You would need the Edgy backports. The regular Multiverse repositories have Flash 7, not Flash 9.

As for the /var/lib/dpkg lock problem--only one program can be using the package manager at a time. If you're using *aptitude* or *apt-get* to access the package manager (*dpkg*), you cannot also have Synaptic Package Manager, Add/Remove Programs, or Adept Package Manager open at the same time.

I would highly recommend that if the only thing you want to install is Flash 9 that you follow these directions:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Otherwise, to learn in general how to install software, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bigmc on 2007-01-20
I closed package manager and things wnet smooth until I tired to get the file.. It connected then got "permission denied"

Getting there..

---

### Post by aysiu on 2007-01-20
> **bigmc said:**
> I closed package manager and things wnet smooth until I tired to get the file.. It connected then got "permission denied"

Getting there..
Can you post the **exact** output of whatever command you did that got denied? Just highlight and copy and paste it here.

---

### Post by Andrew Panin on 2007-01-20
I recommend you to use such a nice tool as EasyUbuntu (if I'm right, [http://easyubuntu.freecontrib.org)](http://easyubuntu.freecontrib.org)). Besides Flash Player, you can easily enable your Ubuntu to understand end play MP3 files, almost all videos and do many other useful things.

Just install "easyubuntu_latest.deb" package that you'll have found on the website ("sudo dpkg -i easyubuntu_latest.deb" in the directory in which you've downloaded the file), find the link appeared somewhere in the Applications menu (for instance, in Kubuntu that's the "Utilities" category) and run it.

Hope, this will help. :-)

---

### Post by bodhi.zazen on 2007-01-20
> **aysiu said:**
> I would highly recommend that if the only thing you want to install is Flash 9 that you follow these directions:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) 

As usual nice how-to Aysiu ;)

Thanks, I will be referring people to that one :p

---

### Post by Quillz on 2007-01-20
You can also go directly to Adobe's site and get Flash Player 9 for Ubuntu (.deb) or openSUSE (.rpm). After downloading the package, just open it and it will automatically gather any dependencies and then install onto your system. It's roughly similar a Windows .exe file.

---

### Post by aysiu on 2007-01-20
> **Quillz said:**
> You can also go directly to Adobe's site and get Flash Player 9 for Ubuntu (.deb) or openSUSE (.rpm). After downloading the package, just open it and it will automatically gather any dependencies and then install onto your system. It's roughly similar a Windows .exe file. There's a .deb? I don't see one (take a look at the attached screenshot of the Adobe page).

> **bodhi.zazen said:**
> As usual nice how-to Aysiu ;)

Thanks, I will be referring people to that one :p I actually need to update it because there wasn't a .deb file when I wrote that, but there now appears to be one in the Edgy backports. I'm going to see if that needs any extra dependencies or not.

---

### Post by Quillz on 2007-01-21
> **aysiu said:**
> There's a .deb? I don't see one (take a look at the attached screenshot of the Adobe page).

 I actually need to update it because there wasn't a .deb file when I wrote that, but there now appears to be one in the Edgy backports. I'm going to see if that needs any extra dependencies or not.
Sorry, I got the .tar.gz mixed up with the .deb. I must be thinking of something else.

---

### Post by aysiu on 2007-01-21
> **Quillz said:**
> Sorry, I got the .tar.gz mixed up with the .deb. I must be thinking of something else.
That's okay. There is a .deb in the Edgy backports, though. Pretty soon I'll update my Psychocats page to reflect that.

**Edit**: The page is updated. It uses the repositories for Edgy Eft and Adobe's .tar.gz for Dapper Drake.

---

### Post by plumeria on 2007-01-21
Whenever I try to install from the psychocats repo it says:
Downloading... download failed
The Flash plugin is NOT installed.

And that's about as far as I get.

---

### Post by aysiu on 2007-01-21
There is no Psychocats repo. Do you mean you Edgy Backports? Can you paste here *exactly* what you typed into the terminal and *all* of what the terminal output was?

Also, have you tried the other method?

---

### Post by bigmc on 2007-01-21
I installed easyubuntu (I think)... Anyway everything went without and error..

Thank-you very much.. You don't get service like this in Windows... I am becoming a convert...:D

---

### Post by Dr.Jim.B. on 2007-01-21
EasyUbuntu is a good suggestion!   The URL is not quite right in the earlier post.  Use  [http://easyubuntu.freecontrib.org](http://easyubuntu.freecontrib.org).  

Hope that helps.  -Jim  

> **Andrew Panin said:**
> I recommend you to use such a nice tool as EasyUbuntu (if I'm right, [http://easyubuntu.freecontrib.org)](http://easyubuntu.freecontrib.org)).

---

### Post by PauloPio on 2007-01-24
> **plumeria said:**
> Whenever I try to install from the psychocats repo it says:
Downloading... download failed
The Flash plugin is NOT installed.

And that's about as far as I get.

The edgy backports installs a .deb file that downloads the flash plugin from the adobe site, but it appears that it is offlline at the moment. I tried even downloading it directly from the site ( [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")  ), no luck either.

---

### Post by bwitte on 2007-01-24
I would highly recommend that if the only thing you want to install is Flash 9 that you follow these directions:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

I just wanted to say that this worked for me also, Thanks everyone

---

