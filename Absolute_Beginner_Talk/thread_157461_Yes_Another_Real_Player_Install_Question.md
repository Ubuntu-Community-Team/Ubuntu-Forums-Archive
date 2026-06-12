---
title: "Yes Another Real Player Install Question"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by John_the_linux_newbie on 2006-04-09
OK - I am a goof. I'm running Breezy on a laptop and just installed onto a desktop.
I managed to install Real Player on the laptop and a week later I seem to have forgotten what I did.

I've been to the help files in the wiki

[https://wiki.ubuntu.com/RealplayerIn...9%7C%28real%29](https://wiki.ubuntu.com/RealplayerIn...9%7C%28real%29)

with no luck. I can get as far as the setup Real screen after downloading from the multiverse. But am stuck at the point at which I need to type the path to the installer. All roads lead back to the type the path screen.

If I try any of the other setup methods in the terminal I get an error that there is a problem finding and installing the support files.

---

### Post by Mustard on 2006-04-09
Can you include information on what command you are currently attempting to do(as shown in the guide) and where the file is actually located on your system that you are attempting to execute this command on?

---

### Post by John_the_linux_newbie on 2006-04-09
Thank you for the reply.
I found the commands I used below at:

[http://help.ubuntu.com/starterguide/C/ch03.html#id2526342](http://help.ubuntu.com/starterguide/C/ch03.html#id2526342)


john@ubuntu2:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by Sef on 2006-04-13
I think that libstdc++5 is not installed. So to install it do this:

sudo apt-get update

sudo apt-get install libstdc++5


then trying to install real player.

---

### Post by John_the_linux_newbie on 2006-04-13
Thank you for the reply.  Since my last post I had the same thought.
I have libstdc++5 installed, but am still having difficulty.

I can begin the real player installation but I don't know how to answer the question about where real player has been download. [Screen Shot 1]("http://www.jniendorf.com/Linux/Linux_Images/download_path.jpg")

if I choose my Desktop or Home directory I get a message indicating that the downloaded file can't be found.  [Screen Shot 2]("http://www.jniendorf.com/Linux/Linux_Images/cannot_find.jpg")

Any ideas?  Thanks.

---

### Post by Sef on 2006-04-13
I see a problem.  You are downloading the one that says .rpm.   You should download the **.deb**.  

Also real player is can be downloaded from Add Applications.  Applications > Add Applications > Sound & Video > more programs > click on real player > Apply > Apply > follow the directions.

---

### Post by cliff0108 on 2006-04-13
I had no end of problems getting the RealPlayer plugin for streaming audio working until I found an answer here about installing the application into the /usr/local directory.
I didn't "uninstall" anything - but just followed the directions below (from the RealPlayer site and from John) and eveything works beautifully now !


[COLOR="Blue"]Go to [http://www.real.com](http://www.real.com) from your Ubuntu box, and click on download
RealPlayer, (there are instructions right below that click'ie.) You
will get the file, RealPlayer10GOLD.bin, in your home directory, maybe
in your Desktop folder.

You will have to have root privileges to install the stuff, so
Applications->Root terminal, and do the following commands:

cp RealPlayer10GOLD.bin /usr/local
cd /usr/local
RealPlayer10GOLD.bin

Look at the installation instructions right below the download
click'ie, and your commands should be something like:
-----------------------------------------------------
Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!
----------------------------------------

at "Continue", press Enter
answer directory is /usr/local/RealPlayer
at a request for finish, F
do not enter mozilla plugins directory, just Enter
configure system wide links, Y, (after the "dots" stop)
the prefix is /usr

That should install RealPlayer.

If RealPlayer won't work out of Firefox, then:

>From your home directory:

cd .mozilla/firefox/plugins
ln -s /usr/local/RealPlayer/mozilla/nphelix.so nphelix.so
ln -s /usr/local/RealPlayer/mozilla/nphelix.xpt nphelix.xpt

and see if that fixes it.

At least that is my best guess.

John[/COLOR]

---

### Post by John_the_linux_newbie on 2006-04-13
Thank you!
I'll give this a shot when I get home from work tonight.

---

### Post by John_the_linux_newbie on 2006-04-14
Thanks Cliff,

Everything worked right up to the point where I should hear music.
Real Player is now installed and launches - I can see stream stats with 0 lost.  The only thing is that there is no sound.  This is odd becasue sound works with everything except Real.  I found a thread on the Helix fourm about OSS drivers.  I installed the OSS downloads from Ubuntu, but still no sound.

---

### Post by cliff0108 on 2006-04-14
Well - that is *some* progress :)
I recall as I was trying this and that to get RealPlayer up I installed Helix as well - I think they are similar and may share sound resources ? (- way over my head here ..) but you could install Helix from Synaptic and see if that effects Real and gives you sound.
You could also check the prferences of the program itslf. Also - I remeber reading advice to deselect the 'sound server' option under System/Preferences/Sounds - don't know why that would amke a difference - but you could try.
Good luck - let me know.
C

---

### Post by John_the_linux_newbie on 2006-04-15
[QUOTE=cliff0108]
Good luck - let me know.
C[/QUOTE]
Well, all the technology in the world won't help anyone if they don't plug it in.
This is embarassing, but I had my speakers plugged into the wrong card - there are two sound cards on this machine.  I'm not sure why, One card did allow me to hear system sounds, but Real Player uses the OTHER sound card.

Thank you for the help - your instructions allowed me to install Real Player - user error caused the lack of sound.

---

### Post by cliff0108 on 2006-04-15
That took courage to admit LOL !
I've done that.
Glad everthing is working - on to the next fun Ubuntu problem solving issue eh?!
C

---

### Post by esteban2x on 2006-04-15
I have followed all the directions and have RA loaded and it's working. However, when I go to synaptic, it says I have a broken whatever ya callit. It's referring to RA. How do I fix this? I tried using the fixit thing with synaptic but to no avail. It wants me to delete the package but I chose not to because I want to use RA.

---

### Post by cliff0108 on 2006-04-15
I would uninstall in Synaptic - then re-install following the instructions I mentioned in my earlier post - see below. This worked for me !


[COLOR="Blue"]"Go to [http://www.real.com](http://www.real.com) from your Ubuntu box, and click on download
RealPlayer, (there are instructions right below that click'ie.) You
will get the file, RealPlayer10GOLD.bin, in your home directory, maybe
in your Desktop folder.

You will have to have root privileges to install the stuff, so
Applications->Root terminal, and do the following commands:

cp RealPlayer10GOLD.bin /usr/local
cd /usr/local
RealPlayer10GOLD.bin

Look at the installation instructions right below the download
click'ie, and your commands should be something like:
-----------------------------------------------------
Installation Instructions from the REal Player page:

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!
----------------------------------------

at "Continue", press Enter
answer directory is /usr/local/RealPlayer
at a request for finish, F
do not enter mozilla plugins directory, just Enter
configure system wide links, Y, (after the "dots" stop)
the prefix is /usr

That should install RealPlayer.

If RealPlayer won't work out of Firefox, then:

>From your home directory:

cd .mozilla/firefox/plugins
ln -s /usr/local/RealPlayer/mozilla/nphelix.so nphelix.so
ln -s /usr/local/RealPlayer/mozilla/nphelix.xpt nphelix.xpt

and see if that fixes it.

At least that is my best guess.

John"[/COLOR]

---

### Post by John_the_linux_newbie on 2006-04-15
Cliff's instructions worked for me.  I didn't need to do anything special for Firefox.  After the installation there was a dialog box that asked me if I wanted to configure  Real Player to work with Firefox - I chose yes.

---

