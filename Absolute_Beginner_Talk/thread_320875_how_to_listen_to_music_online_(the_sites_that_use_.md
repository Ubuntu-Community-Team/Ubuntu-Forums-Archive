---
title: "how to listen to music online (the sites that use real player) ?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-18
how to listen to music online (the sites that use real player) ?  the question sounds simple but the anser is not.

---

### Post by obsidion on 2006-12-18
> **tony2 said:**
> how to listen to music online (the sites that use real player) ?  the question sounds simple but the anser is not.

 Well this worked for me, Install realplayer and its plugins. 

[http://www.real.com/linux/](http://www.real.com/linux/)

 Make sure you read the instructions

---

### Post by tony2 on 2006-12-18
I downloaded the real player installation file. The instructions for instalation are pasted here below as shown in the site. I donot know how to proceed.

> nstallation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

can you tell me how did you install real player and its plugins?

---

### Post by obsidion on 2006-12-18
> **tony2 said:**
> I downloaded the real player installation file. The instructions for instalation are pasted here below as shown in the site. I donot know how to proceed.



can you tell me how did you install real player and its plugins?

Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

 Open a terminal window go to the folder you downloaded it to
and type chmod a+x Real etc, note you don't have to type it all out tab will autocomplete if its unique


- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

 Now if you want to install system wide sudo ./Real etc again use tab to autocomplete enter, answer the questions that come up.


- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

Now assuming you use firefox as your browser cd /usr/lib/firefox/plugins
make sure that the nphelix.xo and the nphelix.xpt sym links are there.
 Other sise you will need to symlink them from where you installed Realplayer
Mine is in /usr/local/real

so to symlink the plugin I would cd to /usr/lib/firefox/plugins and run the commands
sudo ln -s /usr/local/real/mozilla/nphelix.xpt
sudo ln -s /usr/local/real/mozilla/nphelix.so

then ls to make sure they are there. 
Now open firefox and type about:plugins in the address bar to make sure the plugins have been recognised.
If they have it should work fine, I use mine to listen to bbc7

---

### Post by az on 2006-12-18
> **tony2 said:**
> how to listen to music online (the sites that use real player) ?  the question sounds simple but the anser is not.

Does installing Realplayer 10 from the Add-Remove progrmas fix the problem?

Realplay is in the Dapper-commercial and Edgy-commercial repositories.  You can access those repos from the add-remove programs tool.

---

### Post by obsidion on 2006-12-18
> **azz said:**
> Does installing Realplayer from the Add-Remove progrmas fix the problem?

Realplay is in the Dapper-commercial and Edgy-commercial repositories.  You can access those repos from the add-remove programs tool.


 The bbc7 site tended to baulk at the one in the repos it crashed often in the end I uninstalled and installed the version from real, I have had no problems since.

---

### Post by az on 2006-12-18
> **obsidion said:**
> The bbc7 site tended to baulk at the one in the repos it crashed often in the end I uninstalled and installed the version from real, I have had no problems since.

Realplayer 8 (multiverse) or Realplayer 10 (Dapper-commercial)?

---

### Post by mykalreborn on 2006-12-18
you can use songbird([link]("http://www.songbirdnest.com")). it's still in beta version, but it's a pretty good player. it's made on the mozilla platform - like firefox.
check the screencast to learn how it works

---

### Post by tony2 on 2006-12-18
I have downloaded all the repos. now tell me which software i need to download using add/remove to listen to real media files online? thanx.

---

### Post by az on 2006-12-18
> **tony2 said:**
> I have downloaded all the repos. now tell me which software i need to download using add/remove to listen to real media files online? thanx.

RealPlayer 10, see the screenshot.

---

### Post by tony2 on 2006-12-18
the screenshot is taken from ubuntu dapper. I am using ubuntu edgy 6.10 and there is no real player in ubuntu 6.10 repos.

---

### Post by Sammi on 2006-12-18
Anyone know if and how Amarok can do this?

---

### Post by tony2 on 2006-12-18
do you mean to say Amarok can play real audio files online?

---

### Post by zagu on 2006-12-18
Hello there Obsidin, Azz et. al
So I'm trying to get this installed as well.  I'm a newbie too.  I've got both firefox2.0 and firefox1.5  and real installed.  but i cannot get either firefox to see the realplayer plugin.  i've made the symlinks exactly as directed in both the FF 2.0 and 1.5 plugin directories.  I do ls -l and can see them there. No dice.

firefox 2.0 is in $HOME/apps/firefox
firefox 1.5 is in /usr/lib/firefox
realplayer is in /usr/local/real

First of all, do I need to make those symlinks in the 2.0 or the 1.5 plugin directory (or should it matter)? 

***UPDATE***
I finally found the Realplayer package in the repos and am going to try that.  I'll be back when I finish

---

### Post by zagu on 2006-12-18
Also, Obsidion, I found your instructions very helpful.  I didn't follow just one thing.  What did you mean by:

Now if you want to install system wide sudo ./Real etc again use tab to autocomplete enter, answer the questions that come up.

That sounds as if i'm installing RealPlayer10 a second time but what does it mean to "use tab to autocomplete"  etc?

thanks

---

### Post by zagu on 2006-12-18
Hello azz,
I tried that but the Add/Remove programs app is in loop.  It just keeps asking to enable Third-Party Dapper Commercial channel.  Realplayer is visible but I cannot get it to install with this method.  I could manually install it but then the plugins are not found by firefox.
Any ideas anyone?

---

### Post by obsidion on 2006-12-18
[QUOTE=zagu;1902928]Also, Obsidion, I found your instructions very helpful.  I didn't follow just one thing.  What did you mean by:

Now if you want to install system wide sudo ./Real etc again use tab to autocomplete enter, answer the questions that come up.

That sounds as if i'm installing RealPlayer10 a second time but what does it mean to "use tab to autocomplete"  etc?

  I was a little unclear there. You can either run ./Real etc and install to your own home directory
or use sudo ./Real etc and install it to say /usr/local/real so everyone on the system can use it. If you have more than one user this is useful..

---

### Post by obsidion on 2006-12-18
[QUOTE=zagu;1902912]Hello there Obsidin, Azz et. al
So I'm trying to get this installed as well.  I'm a newbie too.  I've got both firefox2.0 and firefox1.5  and real installed.  but i cannot get either firefox to see the realplayer plugin.  i've made the symlinks exactly as directed in both the FF 2.0 and 1.5 plugin directories.  I do ls -l and can see them there. No dice.

firefox 2.0 is in $HOME/apps/firefox
firefox 1.5 is in /usr/lib/firefox
realplayer is in /usr/local/real

First of all, do I need to make those symlinks in the 2.0 or the 1.5 plugin directory (or should it matter)? 


   It matters, it depends on which one you are going to use, do it to both if you are going to use both

---

### Post by zagu on 2006-12-18
Thanks obsidion . . . that worked   !:-D

---

### Post by tony2 on 2006-12-18
is there an alternate for reall player in ubuntu? can mplayer play real media files online? i ask this becouse some body said real player crashes. in ubuntu edgy i do not see real in the repositaries. i see only mplayer and i see amarok

---

### Post by obsidion on 2006-12-18
> **tony2 said:**
> is there an alternate for reall player in ubuntu? can mplayer play real media files online? i ask this becouse some body said real player crashes. in ubuntu edgy i do not see real in the repositaries. i see only mplayer and i see amarok


  Did you add the commercial repo as explained earlier ? You won't see it otherwise.
Mplayer will play real as long as you install the mozilla-mplayer package. The bbc7 site which is the only one I use real player for tends to be choppy with mplayer though. That is why I took the trouble to install realplayer and its plugins.

---

### Post by tony2 on 2006-12-18
obsidion when i installed repos i selected universe, multiverse and restricted. i see mplayer there. can i install it ? or i need real player ?

---

### Post by tony2 on 2006-12-18
I could not install mplayer or mplyaer plugin for firefox. pls tell me how to install .

---

### Post by tony2 on 2006-12-18
is there nobody to anser?

---

### Post by obsidion on 2006-12-19
> **tony2 said:**
> I could not install mplayer or mplyaer plugin for firefox. pls tell me how to install .


  What are you using to install ?
Use synaptic, search for mplayer tick the mplayer and mozilla-mplayer and say yes to the other things it wants to install.
 
 Or easier still open a terminal,  sudo apt-get install mplayer mozilla-mplayer

 You need to go and read this whole thread, you have been told at least once that realplayer is not in the main repos and that you need to enable the commercial one. Personally I don't like mplayer for real media and find it choppy for live streams. I have explained in detail how to install Real Player from the main website another one who joined the thread had no difficulty understanding how to do it from my instructions so I don't think I was being unclear or obtuse.

---

### Post by tony2 on 2006-12-19
finally i installed xmms. now the system is playing mp3 files. but real audio files on the net is not yet played.

---

### Post by tony2 on 2006-12-19
I installed real player but it is installed in my desktop. How to hide or re install it in the system / directory?

in which directory should it be installed normally? how to install it there?

---

### Post by az on 2006-12-19
> **tony2 said:**
> I installed real player but it is installed in my desktop. How to hide or re install it in the system / directory?

in which directory should it be installed normally? how to install it there?

Maybe this will help:

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by obsidion on 2006-12-19
> **azz said:**
> Maybe this will help:

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)


](*,)   Or actually read the replies in this thread, putting in the commercial repo has been mentioned at least twice in this thread. I also wrote a reply outlining how to do it system wide from the realplayer downlaod. Ubuntu is not windows, it does things differently and you need to get your head around that. Yes it is a steep learning curve but you aren't even going to start up that curve unless you read and take note when people try to help you. How or why you installed it on the desktop has me beat, however it will work the trouble is because you didn't install it system wide only you will be able to use it. It also means that the plugins now have to be put or linkied to your own .mozilla/firebird plugin directory.
  As to uninstalling it or hiding it then yes it can be done, how did you install it to your desktop did you follow the real player instructions from their site or did you have others have suggested and the quoted link above outlines enable the commercial repo. As you installed it to the desktop, I think you have used the real download and not followed the instructions properly, go back and read them again, then look at the couple of replies I made to you about how to install it system wide or enable the commercial repo and use synaptic to install it. You keep wandering off on tangents rather than trying to solve THIS problem, like what has xmms and mp3's got to do with your original question ? You asked about mplayer and I told you what to do to get it to play real media, did you try that ? ](*,)

---

