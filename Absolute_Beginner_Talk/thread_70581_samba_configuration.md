---
title: "samba configuration"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by herrpoon on 2005-09-30
Right, I've set up samba and what not, so that on my network at home, the windows machine can at least see some part of my ubuntu box.  The bit they see is /home/herrpoon or whatever but what I want to be able to do is to share individuals folders say  /usr/local/folder_x for example as there's some stuff in there I want to share.  I tried right-clicking and ticking the share option, but it doesn't appear in my network places, do I have to configure samba specifically for this or am I doing something else wrong?

---

### Post by patrick295767 on 2005-09-30
I am even more beginner than you ....


Could you maybe tell me how you start/ set up ur samba ?

I am in a windows network of lot's of pc but cannot see any of them ... 

I dont knwo anythign about seeing windows pc .. 

thx 

pat('

---

### Post by davmac on 2005-09-30
You need to edit your samba configuration file - "sudo gedit /etc/samba/smb.conf".

Once I'd been through the the Samba section in the starter guide ([http://ubuntuguide.org/#sambaserver)]("http://ubuntuguide.org/#sambaserver%29"), I found the best way of understanding the setup was to look at samples of what other people use. A quick google for "sample smb.conf" will find plenty for you.

HTH,

Dave Mac

---

### Post by herrpoon on 2005-09-30
Thanks will do, just wanted to make sure it was something I hadn't configured as opposed to something I had screwed up :rolleyes:

-all sorted, wasn't a problem really, just made a link to the folder

---

### Post by patrick295767 on 2005-09-30
thx for informations ... after one hour of studies in the ubuntu guide ... 
I understand a shit to the samba 

I have to buy a book a guess to find out..

thanx anyhow

I also have broken sources.list ... 

is there someone who could give a copy of his /etc/sources.list ... 

thx 


Pat'

---

### Post by davmac on 2005-10-01
Patrick,

Don't give up hope. I'm sure we can get you through this! :)

Are you using warty, hoary or breezy? If hoary then you can use the sample sources.list from [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories").

So have you installed samba and smbfs? If not, open up a terminal and type "sudo apt-get install samba smbfs"

If you then edit the samba configuration file - "sudo gedit /etc/samba/smb.conf" and look for the line that says "workgroup =". Make sure the value here matches the network name set up on the windows machine. From memory, you can check this by right clicking on "my computer" and choosing properties, and then its on one of the tabs you're presented with.

Save smb.conf and then restart samba by typing "sudo /etc/init.d/samba restart".

Then if you click Places -> Network Servers, what do you see?

Regards,

Dave Mac

---

### Post by gw90se on 2005-10-01
[QUOTE=patrick295767]
I also have broken sources.list ... 
is there someone who could give a copy of his /etc/sources.list ... 
thx 
Pat'[/QUOTE]

Ouch, I too learned the hard way in the beginning why they state to make a back up copy first. I thought, "Hey, I;m just adding a couple of lines of text. I can always delete those.":-\\\

---

