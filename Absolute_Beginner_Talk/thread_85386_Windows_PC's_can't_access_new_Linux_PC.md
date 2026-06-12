---
title: "Windows PC's can't access new Linux PC"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by Scottova on 2005-11-02
I am a complete newbee to the world of Linux (and user forums) so please be patient with me.

I have built a new PC, AMD xp2200 PC chips Motherboard 256mb.

Loaded Ubuntu 5.10 Breezy Badger, last week, no problems at all, the system found all the hardware, what a pleasure!  Made me a Linux convert, but I guess everyone goes through that! 

I was able to download the decoaders to make the media players work, my first successful "Linux prodject." 

Now that I have a desktop system working I am trying to expand what I'm doing and learn Linux as I go.

My next step (this is where I'm having problems) is to use this Linux maching as a file and print server for the home LAN.

I have installed SAMBA, and am now able to see all the machines from both the Linux box and the "Windows workgroup" and am able to access both Windows XP PCs on the LAN and shared folders on those PC's without any problems from the Linux box.
 
However, when I try to access the Linux machine from either PC I get a pop-up "Connect to Localhost.localdomain" dialog box.  

I have tried loging on, using all 3 user accounts that I set-up on the Linux box but the PC responds with another pop-up "Connect to Localhost.localdomain" dialog box, with the {PC's name}/userid and password filled it.

I have no idea what I did wrong!  Is it possible that I have configured something in SAMBA or is there something I have to add to the Windows configurations to make this work?

Thanks in advance, Scott

---

### Post by KingBahamut on 2005-11-02
try 

\\ipaddress\share 

with username and pass

Sounds like a local DNS issue.

---

### Post by Scottova on 2005-11-02
Bill:
I'm a complete newbee here, and don't understand your reply....
How and where do I try \\ipaddress\share ?

Do I open a terminal window and just type it in?

Sorry about asking the dumb questions, I really appreciate the assistance.

I guess I need to lean the "linux alphabet" before trying to "speak" about the problems I'm having.  I guess this is the way to learn, as long as you Linux people are patient with us "recreational" user's questions. 

Regards,
Scott

---

### Post by matthewv on 2005-11-02
I think he means try to type in the adress bar of windows explorer or whatever you're using to try acess these shares \\ipaddress\share Where ipaddress is the ip address of your linux box and share is the name of the share you are trying to access.

---

### Post by Scottova on 2005-11-02
I went to internet explorer and typed \\{Ipaddress of Linux box}\share and the login popup dialog started again.

Another stupid question, just to show how new all this is to me...  How do I set up a directory to share?

Thanks
Scott

---

### Post by KingBahamut on 2005-11-02
rclick on the folder and click share folder. 

Youll have to be sure as well, the username you use is on smbusers. 

best way to do this is to do an 

sudo smbpasswd <username> 

once that is set, use that username and pass when asked for such during access.

---

### Post by Scottova on 2005-11-03
Bill:
Thanks!  
I was able to add one username and password to the smbpasswd and am now able to access the linux box through both XP boxes!

Now I'll try to add additional users/passwords to the Linux box!

---

