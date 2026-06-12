---
title: "setting up a fileserver"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by jonl on 2007-07-18
Hi
I am new to ubuntu and have just installed the serverversion of feisty fawn on my servercomputer, and the desktopversion og edgy eft on my laptop. How do i set up the server so i can connect the  laptop to the server and start to share files in my network?

Thanks, JonL

---

### Post by AZzKikR on 2007-07-18
> **jonl said:**
> Hi
I am new to ubuntu and have just installed the serverversion of feisty fawn on my servercomputer, and the desktopversion og edgy eft on my laptop. How do i set up the server so i can connect the  laptop to the server and start to share files in my network?

Thanks, JonL

This can be done using samba. Install samba and smbfs using apt-get on the server computer, and configure it to share whatever directory you want to get shared. Then, install samba and smbfs on the laptop, then you can make connection to the server using the mount command, or through the 'Places' menu. 

It is quite a big topic to just quickly tell it here in a few steps. Check out [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server"), it helped me starting up a Samba server. Feel free to post more questions about this if needed.

---

### Post by MythicalVax on 2007-07-18
Well, when I start from scratch, I am following this order:[LIST=1]
[*]**ftp** (vsftp for the server side, gftp for the client one): it is a matter of minutes for both sides.
[*]**ssh** to get a secure terminal access and another transfer mode (gftp as a client again is nice, but you could even _mount the ssh file system_)
[*]**nfs** or **samba** or **openafs** for a true file sharing session: I would start from an easy unauthenticated anonymous samba sharing configuration just to accomplish a cross platform solution[/LIST]Oh, I would not forget to give **X** a try to connect to the server: in this way you would have a GUI without even having one on the server... (but this may be strange and a bit difficult if you haven't seen it before) The X access to the server might help you getting comfortable with some sharing info under System->Administration (GUIs are not so bad, indeed)

If you like command line, give **z-shell** a try, too. it is easy to get file transfers between two computers running z-shell and it is far better than bash...

Personally, I have adopted samba as my favourite default file sharing method and I have been using it for months to look at movies and to read ebooks I have saved on the server and it is working great in a 10/100 Mbits LAN. It is so good I am thinking to upgrade to a Gbit LAN since I cannot think of being without it any more... and I have been constantly adding services and resources...
Linux and in particular Ubuntu is great at networking and file sharing....
(When everything will work, do not forget to give **hamachi** a try: that will allow you to share in a vpn!!)

---

### Post by az on 2007-07-18
> **jonl said:**
> Hi
I am new to ubuntu and have just installed the serverversion of feisty fawn on my servercomputer, and the desktopversion og edgy eft on my laptop. How do i set up the server so i can connect the  laptop to the server and start to share files in my network?

Thanks, JonL

The easiest way woudl be to install ssh on the server and to make an idon on your desktop to connect via ssh to the server.  Click on connect to server and pick ssh, the  address and username.

Click on the icon that creates and you will get a nautilus windows with your files from the server.  

That's really the easiest way to share between two linux boxes.

---

