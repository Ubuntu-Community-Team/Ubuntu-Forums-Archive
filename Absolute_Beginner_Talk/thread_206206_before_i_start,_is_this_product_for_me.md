---
title: "before i start, is this product for me?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by killtheoldman on 2006-06-29
hey people, This is my situation, 

I have 7 windows 2000/xp machines I'm using to run 6 windows based database programs. I have a peer to peer network and its causing some packet loss problems. 

I have very little experience in running file servers but I need to set this up, ideally just on one PC using as a file server, which will interact with the windows xp / 2000 machines,  before I go about trying to educate myself on how to do this. Can anyone tell me, is this the product for me, if so can you point me in the direction of where to start.

---

### Post by shoot2kill on 2006-06-29
that is a very broad question....

i could say "Ubuntu will work fine with your requirements..."

i could also say "Windows will work fine for your requirements..."

is there any other programs that u need to use to run ur business.....

any more requirements

---

### Post by uzi09 on 2006-06-29
please see "Is Ubuntu for me?" sticky located at the top of this forum
here's a link:
[http://www.ubuntuforums.org/showthread.php?t=63315](http://www.ubuntuforums.org/showthread.php?t=63315)

---

### Post by killtheoldman on 2006-06-29
Thank you ,UZI I did read the stiky. I didnt not see the answer i was looking for. It  May be due to my lack of understanding with the nature of file servers. 

This is my question, if the program files are located on the ubuntu server, and accessed by the winows machine do the programs themselves need to be compatable with linux inorder for them to operate with the client side windows machines. 

none of these programs are anything that anyone here would have ever heard of the names of the Programs are  CCIRater Prorater.exe, a database made in the office using the MS access, Papervision - an file image database written in ASP, Choices database, 

other than that its just a bunch of .xls and .doc files that people will need acces of. 

I appreciate you patience with me as I am a newbie of newbies (or at least i feel that way)

---

### Post by shoot2kill on 2006-06-29
then im not sure, i thought u was lookin to make all of the syatems ubuntu...

?????????????????

---

### Post by uzi09 on 2006-06-29
if you're talking about application sharing between a linux server and windows clients...

yes, the app has to be able to run in linux for the clients to be able to use them.

---

### Post by steve.horsley on 2006-06-29
[QUOTE=killtheoldman]Thank you ,UZI I did read the stiky. I didnt not see the answer i was looking for. It  May be due to my lack of understanding with the nature of file servers. 

This is my question, if the program files are located on the ubuntu server, and accessed by the winows machine do the programs themselves need to be compatable with linux inorder for them to operate with the client side windows machines. 

none of these programs are anything that anyone here would have ever heard of the names of the Programs are  CCIRater Prorater.exe, a database made in the office using the MS access, Papervision - an file image database written in ASP, Choices database, 

other than that its just a bunch of .xls and .doc files that people will need acces of. 

I appreciate you patience with me as I am a newbie of newbies (or at least i feel that way)[/QUOTE]

This will not be a problem. A file server's job is to store files. If the Windows machines put windows files on the server, they will be able to retrieve those files and run them. They will never know what operating system the file server is running - they just say "save this file" or "fetch this file" and the server does so.

---

### Post by Apple 101 on 2006-06-30
Will you need to run an Exchange server or anything like that?

---

### Post by killtheoldman on 2006-06-30
no im pritty shure I wont have to, Now there is that program that runs in asp, im wondering if that is a compatable program, ubuntu uses apache correct?

---

### Post by cjssmo on 2006-06-30
I have a question for you, are your windows machines running Windows XP Pro or XP home edition, If you are running Windows XP Pro you will not have any problem connecting all your machines together for file sharing through samba, Windows XP home edition does now support this (all you get is simple file sharing with windows xp home edition) which will not allow it to sign onto a samba server.  But yes ubuntu can be setup as a file server.  I currently have two servers on my lan, an mp3 server and a photo server.  If they are only going to be on you lan then it should be pretty easy to set it up.  There are a ton of howto's out there on how to set up a server, the debian site has  a good one.

---

### Post by killtheoldman on 2006-06-30
all xp are win xp prof, could you provide a link to a how to that you would recomend for my obvious lack of expertise, 

I want to partition my drive so i can save the current OS info and just work off the partition is there anything I need to know about that, other than that I will begin the exploration hopefully sunday

---

### Post by Apple 101 on 2006-07-01
Correction to what cjssmo said, XP Home can connect to Samba servers.  Open Synaptic, and search for Samba and Swat.  Install them, and then run the Swat utility (can't remember how) but I remember it is a web-based configuration.

---

