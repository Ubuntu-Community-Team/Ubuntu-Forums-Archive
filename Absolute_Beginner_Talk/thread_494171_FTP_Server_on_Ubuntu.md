---
title: "FTP Server on Ubuntu"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by delongt on 2007-07-06
HI
 I run a photo lab in a busy part of San Diego where parking is a nightmare. I'm looking for a way to set up an FTP server using Linux (with Ubuntu or another Linux OS) so my clients can upload there files and orders to us. That way they will only have to make 1 trip to us to pick up their order. 
Nothing to fancy. Just something my clients can log on to any time and upload their files. I'm already using  server software on a windows xp  system but that box is having problems and so is the software. 
Does anyone have a suggestion on a good ftp server software for Linux. It needs to be pretty easy to set up or at least come with good detailed instruction on how to set it up.  Has to be compatible with a windows network. Mac and Windows users have to be able to log on to it with out any problems. 

Thanks
Terre

---

### Post by Swab on 2007-07-06
I use VSFTP, it's available for install in the Ubuntu repositories!  There is also ProFTP (I think that's what it's called) but I haven't tried that.

Whatever you choose there should not be any compatibility issues with Windows or Mac.  FTP is a standard protocol.

---

### Post by Raineer on 2007-07-06
Yup, vsftpd is as easy as it gets, and works awesome.

```
sudo apt-get install vsftpd
```

[This]("http://www.netadmintools.com/art355.html") is a good site for config info

---

### Post by delongt on 2007-07-06
Sorry, I'm a Linux newbie. Do I go to the terminal and type the above command or do I have to download the application first?

---

### Post by Raineer on 2007-07-06
Yeah you can just open a terminal and type that in, that's the best way as you can see any error messages.

For a lot of console commands you could also do Alt-F2 which opens up a command prompt, but I would do this from a Terminal.

---

### Post by Cypher on 2007-07-06
You can type that command in the Terminal or go to the Synaptic Package Manger under System->Administrator and find the FTP packages there.

Realize that you'll have to create users on your system for all of your clients and then they will be able to FTP their files over. You're really looking for a Web front-end that would allow users to register themselves and send  files to their accounts and for you retrieve from the back end.

I think the FTP solution will be limiting..

---

### Post by delongt on 2007-07-06
Yeah I know the ftp solution will be limiting. Right now I'm just doing this for 20 or so of my biggest customers. I've had a server running like this for 2 years now with about 40 regular customers on XP but for some reason, in the last few months, it's dropping connection.  We will eventuly get our website updated and hope to incorporate  a web front end like you mentioned. 
Thanks
Terre

---

### Post by Cypher on 2007-07-06
Ahh Ok..if you've already established this sort of system on Windows, replicating it in Linux will be easy (and hopefully more stable)..

Good luck..

---

### Post by neander on 2007-07-08
I used synaptics to install (I guess) vsftpd on ubuntu 6.10. The little checkbox is now green in synaptics and offers only to update or remove so I guess it went ok. But how do I use vsftpd? I don't see anything like a entry point in any of the ubuntu menus. Is this command line only? The vsftpd website has a docs section that is useless for install or config, as far as I can tell, the discussion forum listed is unavailable. 

I'm looking for  a very simple to configure ftp server so that I can move files over to the ubuntu box, if there is an ftp server that is simpler for a ftp and linux novice to work with, please let me know.

---

### Post by robertc36 on 2007-07-08
I use GFTP to move files between ubuntu and XBMC has a quick connect option which is all i use.
Very easy to get to grips with.

---

### Post by Raineer on 2007-07-08
I posted a link up above on configuring, maybe you didn't see it?

The web pages aren't useless for configure or install.

#1, it's already installed as you did that under synaptic (yes, it's that easy)
#2, you configure it by editing /etc/vsftpd.conf   (there's enough comments IN the config file you don't even need instructions)
#3, you start it with the command ```
sudo /etc/init.d/vsftpd start
```

Don't give up and assume this isn't the solution this easily, you won't make it far in Linux ;)  By the way most services and "server" type apps (web pages, telnet/ssh, vnc) all work just like I stated above.

---

### Post by neander on 2007-07-08
That's an gftp is ftp client as far as I can tell, I need a server.

I seem to have vsftpd running now. However I can't edit the config file. Honestly linux is a headache when you rarely use it. I have natilus set up to open as root but if I open the config file with it it's read only. If I sudo gedit, I have no access to the etc folder.

---

### Post by neander on 2007-07-08
I couldn't find anything that walks a newbie through an install or config process, so useless they are to me. I'm sure if you want to see how secure vsftpd is or how fast it is, the website is useful.

Eventually I'll re-figure out how to edit a text file in linux that is not in my user dir. Once past that hurdle, some parts of the conf are clear. But I'm not sure about a main point, which is how to set up a user so they can upload. I will disable anon access. But setting up a user so they can upload..I have no idea. I suppose if I knew a lot about ftp it's be plain?

---

### Post by neander on 2007-07-08
it looks like gproftpd with proftpd will be simpler for a newb like me, so no need to post more instructions re vsftpd. But I'm still curious as to how to edit a text file, that's going to come up again

Thanks

---

### Post by Raineer on 2007-07-08
Open a terminal (it's in the menus under System Tools, or press Alt-F2 to open a command line window:
```
sudo gedit /etc/vsftpd.conf
```

Sorry, from the way you talked I thought you knew a bit more about Linux.  gftp IS a client, you're right about that, you need something like vsftpd (it does help when someone reads the question before replying). Anyways, I just walked you through the process above.

I did go back and look at that link, it is exactly starting and configuring it, although I guess it's a little short if you need every single step spelled out exactly (like how to edit the file).  Again, you have it installed because you did that through synaptic.

---

