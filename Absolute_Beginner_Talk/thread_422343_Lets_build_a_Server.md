---
title: "Lets build a Server"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by koclea on 2007-04-25
Hi

OK, so I have downloaded ubuntu server, created my CD.  I installed the first option, that just led me to a login prompt and then well nothing...just a command line.  So, then I installe dthe 2nd option "Install LAMP server", ended up with the same thing.  So does Ubuntu just give you a login prompt and no GUI?  am I missing something, there has to more to Ubuntu than that (I hope)

look forward to some replies and or/help.

PS. I put it on a brand new PC to see how it all works before I build my Dell server with it.

---

### Post by darkrose on 2007-04-25
The server edition does not include a gui, if you want a gui you'd be better off with the desktop edition.

Also you can install webmin which would enable you to administrate the server from another computer over the net.
Here's a little how to for installing webmin: [http://ubuntuforums.org/showthread.php?t=7507](http://ubuntuforums.org/showthread.php?t=7507)

---

### Post by koclea on 2007-04-25
So what is the recommendation then?  I am thinking of using Windows server 2003 (as I have some Windows knowledge) but I thought I would try out Ubuntu first.  Do I need a server version of Ubuntu to do file serving and account administartion on windows clients, or can I doo all with Desktop Ubuntu?  I would really like to get started on the right foot here.  Thanks

---

### Post by Sef on 2007-04-25
You could add a gui to your server.

From the terminal, type these two lines:

```
sudo aptitude update
```

```
sudo aptitude install ubuntu-desktop
```

---

### Post by Skrynesaver on 2007-04-25
Traditionally Linux servers don't run a GUI, this alows them devote their resources to *real* work as opposed to drawing pictures.  As most production servers are administered remotely the command line is the fastest and most efficient way to do things.
If you aren't that familiar with the command line administering a server will involve a lot of learning.  However this learning is a good thing ;) it will also make you a more efficient user.  There are many sites that take you through the basics but 
```
man -k  <keyword>
```
Should find related commands, then man the command to find out about it's operation.
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
May prove helpful setting up various services.  Have a lot of fun as my former distribution used to say

---

### Post by meney on 2007-04-25
I would do that, use the server edition and then add the gui. This way you will have all the proper packages installed, as opposed to just the desktop version.

Ubuntu works well as a server, but if you are going to use linux as a server (very powerfull option) it is best to familiarize yourself with the command line a little bit.

---

### Post by igknighted on 2007-04-25
Keep in mind the cost involved with Windows Server 2003 and all the related apps... thousands of dollars (US) at least if you are doing it legally.  A Ubuntu LAMP setup is really easy.  I set up one in a couple hours last week knowing absolutely nothing.  Basically I set it up, dropped a website in the proper folder, configured my router to forward port 80 (html requests) and ftp to the server box set up as a static IP and voila.  Getting my domain name was the hardest part, and that doesn't matter about windows/linux etc.

If you are new to linux the hardest part will be learning permissions, even as a linux veteran the permissions in /var/www messed me up a little.  Overall, I think its an easier task to learn it than you might imagine.  Webmin is easy, and if you get more comfortable SSH and Putty will be your friends.  You could turn it on and leave it be, and never reboot it for a year if you don't want.

---

### Post by kvonb on 2007-04-25
> **koclea said:**
> So what is the recommendation then?  I am thinking of using Windows server 2003 (as I have some Windows knowledge) but I thought I would try out Ubuntu first.  Do I need a server version of Ubuntu to do file serving and account administartion on windows clients, or can I doo all with Desktop Ubuntu?  I would really like to get started on the right foot here.  Thanks

No you don't actually NEED the server version of Ubuntu, the desktop version will do everything that the server version can do.  I believe the only differences are that the server version does not come with the GUI, because most server uses don't need it, and/or don't want it because of space/size constraints.  And the server kernel is optimised for server tasks, rather than including all the unnecessary desktop stuff.

Which on a fast(ish) computer (ie P3 or better) with lots of RAM (256megs+) and HDD (4gigs+)  space, you won't have to worry about.

FIle serving (smb, or samba as Windows file sharing is called), will work perfectly, and once you get the hang of editing the config file, is a damn site easier (in my opinion) than the WIndow-esque "wade through pages of nonsensical variables in a registry database type thing and try to find the right button to click on" way of doing the same job :).

As for web server with PHP and *SQL, again very easy, and also creating your own e-mail server is fairly straightforward too :).

Here is a link with tons of useful stuff:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html)

If you are prepared and able to learn a different way of doing things, go ahead and read that guide, just pick one simple subject like file sharing and work on that before progressing onto more complex stuff.

That way you won't fry your brain with information overload.

And you always have this forum to ask for help, as long as you are polite, you will get all the help you need.

If you don't think you can cope with Linux, go and buy Windows server, it may be the better option for you :).

---

### Post by koclea on 2007-04-26
I got the GUI installed as per previos thread and I thought I was away and running.  But then configuring samba using a text editor to edit /etc/samba/smb.conf.  That spun me out, then I couldnt even save the file.  Then I figured out i can use sudo gedit smb.conf but you still have to know what you are doing in there.  Basically I just need my windows XP PC's to be able to save their files to this sever and use it for user authentication.  I dont want to bag Linux but I always heard it was hard because it was command driven (now I know they were right).  I think I'm in over my head trying to do this with Linux. (sigh). I'm very tired...

---

