---
title: "Remote Connection"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2005-12-27
Newbie Here1?1

I was wondering if anybody out there knew how to set up remote connection
in Ubuntu. I want to be able to control my pc from anywhere on the internet. I used to use Radmin ([http://www.radmin.com/](http://www.radmin.com/)) to connect to my windows(bleH) machine but what program do I use for ubuntu? How do I do it. Any programs I could use, I've heard about realVNC but really don't want to use it.(I tried it in windows(bleH) but didn't like it. 

Any help needed. Fast1?1

 :ph34r: Jaygo333 :ph34r:

---

### Post by Imexius on 2005-12-27
Try ssh, now im not quite sure how to create a server for ssh, personally I wouldnt use it as it is potentially unsafe. To connect using ssh just go "ssh <ipaddressgoeshere>"

Note this is in terminal so if you want a gui i suggest vnc.

---

### Post by Jaygo333 on 2005-12-27
[QUOTE=Imexius]Try ssh, now im not quite sure how to create a server for ssh, personally I wouldnt use it as it is potentially unsafe. To connect using ssh just go "ssh <ipaddressgoeshere>"

Note this is in terminal so if you want a gui i suggest vnc.[/QUOTE]


How do you do it?

:ph34r: Jaygo333 :ph34r:

P.S. You have a nice desktop. How do you change everything.

---

### Post by harisund on 2005-12-27
A couple of questions --
--> "I want to be able to control my pc from anywhere on the internet"
What exactly do you mean by that? Do you have data on it that needs to be accessed? Or do you just want to check up on something once a while? Do you need a graphic user interface or is the terminal enough for you? 
--> "I tried it in windows(bleH) but didn't like it"
What is it that you didn't like about VNC? Is it the speed? 
--> Now, what kind of internet connection do you have?
If you have a fast internet connection, I don't see a problem with VNC. But ssh is a great idea, since I use it all the time. SSH allows you to remotely connect to a terminal through a command line. You can then run your commands from your local machine and it would work on the remote machine as if you were sitting right in front of it. 

However, if you do want graphics, SSH allows that too. But let's leave that for later. 

To start using SSH, basically all you need to do is
apt-get install openssh-server. 

Then on your local machine you can remotely login. 

OK, so if things are not clear, here are some details you can answer for furthere information here: 

1. Why do you want access to your remote machine? Data transfer? Check email? 
2. What kind of internet do you have? In other words, how exactly is your remote machine connected? If it is directly connected to the internet, things are easier, but if you have a firewall or a router, things need to be configured. 
3. From what operating system do you want to login? Are you currently running Windows and want to "setup a remote connection to Ubuntu"? Or do you want to remotely connect from another Linux machine?

---

### Post by harisund on 2005-12-27
A couple of questions --
--> "I want to be able to control my pc from anywhere on the internet"
What exactly do you mean by that? Do you have data on it that needs to be accessed? Or do you just want to check up on something once a while? Do you need a graphic user interface or is the terminal enough for you? 
--> "I tried it in windows(bleH) but didn't like it"
What is it that you didn't like about VNC? Is it the speed? 
--> Now, what kind of internet connection do you have?
If you have a fast internet connection, I don't see a problem with VNC. But ssh is a great idea, since I use it all the time. SSH allows you to remotely connect to a terminal through a command line. You can then run your commands from your local machine and it would work on the remote machine as if you were sitting right in front of it. 

However, if you do want graphics, SSH allows that too. But let's leave that for later. 

To start using SSH, basically all you need to do is
apt-get install openssh-server. 

Then on your local machine you can remotely login. 

OK, so if things are not clear, here are some details you can answer for furthere information here: 

1. Why do you want access to your remote machine? Data transfer? Check email? 
2. What kind of internet do you have? In other words, how exactly is your remote machine connected? If it is directly connected to the internet, things are easier, but if you have a firewall or a router, things need to be configured. 
3. From what operating system do you want to login? Are you currently running Windows and want to "setup a remote connection to Ubuntu"? Or do you want to remotely connect from another Linux machine? 

And Imexius, why did you say SSH is potentially unsafe? Any particular reason?

OOps sorry.. didn't know why 2 postings came about.. does anybody know how to delete a post?

---

### Post by Jaygo333 on 2005-12-28
[QUOTE=harisund]A couple of questions --
--> "I want to be able to control my pc from anywhere on the internet"
What exactly do you mean by that? Do you have data on it that needs to be accessed? Or do you just want to check up on something once a while? Do you need a graphic user interface or is the terminal enough for you? 
--> "I tried it in windows(bleH) but didn't like it"
What is it that you didn't like about VNC? Is it the speed? 
--> Now, what kind of internet connection do you have?
If you have a fast internet connection, I don't see a problem with VNC. But ssh is a great idea, since I use it all the time. SSH allows you to remotely connect to a terminal through a command line. You can then run your commands from your local machine and it would work on the remote machine as if you were sitting right in front of it. 

However, if you do want graphics, SSH allows that too. But let's leave that for later. 

To start using SSH, basically all you need to do is
apt-get install openssh-server. 

Then on your local machine you can remotely login. 

OK, so if things are not clear, here are some details you can answer for furthere information here: 

1. Why do you want access to your remote machine? Data transfer? Check email? 
2. What kind of internet do you have? In other words, how exactly is your remote machine connected? If it is directly connected to the internet, things are easier, but if you have a firewall or a router, things need to be configured. 
3. From what operating system do you want to login? Are you currently running Windows and want to "setup a remote connection to Ubuntu"? Or do you want to remotely connect from another Linux machine? 

And Imexius, why did you say SSH is potentially unsafe? Any particular reason?

OOps sorry.. didn't know why 2 postings came about.. does anybody know how to delete a post?[/QUOTE]

Its OK,

Well, I want to conncet remotely because I have a tendancy to do work better if I connect remotely.  If I'm at home, all I do is play games and can't stop myself. I connect remotely to do homework and sometimes transfer data. 
My internet speed is around 1.5 Mbps. When doing bittorrent get speeds of up to 250kbps sometimes.
 I am behind a firewall but that's easy to configure.(Can do it blind folded.) 
I tried to install the ssh above but got the error. -[ E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory] Any help. 
 I am currently trying to convert wholly into ubuntu but just want to have a remote connection open all the time. I am a forgetful person and almost always leave my information on my home pc and connected to it easy when I had windows. I just want the same capabilities. Transfer and GUI Control. 
I've heard of SSH, how do you configure it to run on your pc. 
I never said there was anything wrong with VNC. I just said taht when I used to use it in my early days of remote connection (I had slower speed then 385k, I just didn't click into it. I could use it if necessary.

I hope taht answered all of your questions.

:arrow:h34r: Jaygo333 :arrow:h34r:

P.S. Just one thing, How do you install any program into your filesystem(harddrive) 
I installed ubuntu but it seems to be installed into my desktop. I want it in the drive. Like in windows in the Program Files folder, not desktop. To run azureus, I use the commands: 
jaygo333@Ubuntu:~$ cd Desktop/
jaygo333@Ubuntu:~/Desktop$ cd azureus/
jaygo333@Ubuntu:~/Desktop/azureus$ ./azureus
Starting Azureus...
then it continues. as you can see, it is installed at my desktop. I don't want that . I want it in my harddrive harddrive.
How do I also install into the harddrive, anything. I tried installing java like the website ([http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting))
said but couldn't access or install in the usr directory. Said I wasn't ?root?
I thought I was ROOT.

Sorry everything is all jumbled up, Didn't have time to arrange.
Any help greatly appreciated1?1

---

### Post by Imexius on 2005-12-28
Just go to system-->preferences and edit those to change your desktop

---

### Post by harisund on 2005-12-28
First, to install any software you need to have administrator previledges in your computer. In linux, that means you need to become the "root" user to install. 

Type ```
sudo apt-get install openssh-server
``` and SSH server is installed. Then you can access the machine through SSH from any other computer that has the SSH client installed. ```
ssh <ipaddress of remote machine>
```. If you want to do further configurations, like change the port on which SSH listens to, then look into */etc/ssh/sshd_config* or something that is similarly named. 
I would suggest you search for something called automatix in these forums. That installs a lot of software for you, including both java and azureus. 
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by mscman on 2006-01-15
[QUOTE=harisund]
And Imexius, why did you say SSH is potentially unsafe? Any particular reason?[/QUOTE]

Just wanted to point out to anyone reading this post, ANY remote connection to a computer is potentially unsafe if a strong password isn't used.  Make sure to keep that in mind if you have important data on your computer.

---

### Post by hen3rz on 2006-01-15
hello,

i use vnc all the time and its great, although it is a little unsafe..

this guide is very helpful and i think will answer your question:

[http://ubuntuguide.org/#remotedesktop]("http://ubuntuguide.org/#remotedesktop")

---

