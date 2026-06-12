---
title: "How do i get the best media player?"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by Mathias-K on 2005-10-20
Hi, i'm progressing in converting my main computer to a linux station. MP3-files are now playing nicely in Beep, so that's no problem, now video is my main obstacle.

I mainly have MPEG's and DivX AVI's, and i was normally using Windows Media Player. None of the programs i have tried (Beep, XMMS and some other) seem to be able to play AVI's, and do only play MPEG's without sound. So i went for a Linux-version of DivX, but all i got was a package of .h, .sh and .so-files, and how do you install them? :confused:

After that i tried VLC Media Player which is downright ugly, Win9x-ish and boring, so my question is which media player is the best, and how in the world do i get it?

Thanks in advance, Mathias

---

### Post by patrick295767 on 2005-10-20
[QUOTE=Mathias-K]Hi, i'm progressing in converting my main computer to a linux station. MP3-files are now playing nicely in Beep, so that's no problem, now video is my main obstacle.

I mainly have MPEG's and DivX AVI's, and i was normally using Windows Media Player. None of the programs i have tried (Beep, XMMS and some other) seem to be able to play AVI's, and do only play MPEG's without sound. So i went for a Linux-version of DivX, but all i got was a package of .h, .sh and .so-files, and how do you install them? :confused:

After that i tried VLC Media Player which is downright ugly, Win9x-ish and boring, so my question is which media player is the best, and how in the world do i get it?

Thanks in advance, Mathias[/QUOTE]

my best player is MPLAYER

apt-get install mplayer-386 

is damn fast and good enough for me ...

---

### Post by Manny C on 2005-10-20
[quote=Mathias-K]Hi, i'm progressing in converting my main computer to a linux station. MP3-files are now playing nicely in Beep, so that's no problem, now video is my main obstacle.

I mainly have MPEG's and DivX AVI's, and i was normally using Windows Media Player. None of the programs i have tried (Beep, XMMS and some other) seem to be able to play AVI's, and do only play MPEG's without sound. So i went for a Linux-version of DivX, but all i got was a package of .h, .sh and .so-files, and how do you install them? :confused:

After that i tried VLC Media Player which is downright ugly, Win9x-ish and boring, so my question is which media player is the best, and how in the world do i get it?

Thanks in advance, Mathias[/quote] 
If you are using Gnome, try [Banshee Music Player]("http://www.banshee-project.org/index.php/Main_Page"):
```
sudo apt-get install banshee
``` 
If you are using KDE, try [Amarok]("http://amarok.kde.org/"):
```
sudo apt-get install amarok
``` 
Both rock the house. Oh, and make sure that your [universe repositories are enabled]("http://ubuntuguide.org/#extrarepositories") (for Banshee to be available using apt-get).

---

### Post by Mathias-K on 2005-10-20
[QUOTE=patrick295767]my best player is MPLAYER

apt-get install mplayer-386 

is damn fast and good enough for me ...[/QUOTE]

I must say that if i ever thought that parts of Windows were ilogic, DOS-like and unnessecarily complex, then Linux has made me forget all that!

When i copy paste your code into the terminal, i get the followong error:

[I]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/I]

Aha, i thought, i'll just write "sudo" in front of it and then type my password. What happens then? I'm prompted for the password, but then i'm unable to type it.. Well...:confused: 

The developers of Linux seem brilliant, so why don't they just abandon this dusty DOS-mania and make it all automatic in the package manager or as a .tar-installer?

Regards, Mathias

---

### Post by Manny C on 2005-10-20
[quote=Mathias-K]
Aha, i thought, i'll just write "sudo" in front of it and then type my password. What happens then? I'm prompted for the password, but then i'm unable to type it.. Well...:confused: 
[/quote]

The password is deliberately not displayed. No hashes or characters. Simply type in the password (you won't see if being displayed).

---

### Post by Mathias-K on 2005-10-20
[QUOTE=Manny C]If you are using Gnome, try [Banshee Music Player]("http://www.banshee-project.org/index.php/Main_Page"):
```
sudo apt-get install banshee
``` 
If you are using KDE, try [Amarok]("http://amarok.kde.org/"):
```
sudo apt-get install amarok
``` 
Both rock the house. Oh, and make sure that your [universe repositories are enabled]("http://ubuntuguide.org/#extrarepositories") (for Banshee to be available using apt-get).[/QUOTE]

Thanks, but as i wrote in the other reply, my Terminal is getting screwy on me. I cannot write anything, when i'm prompted for the password!:confused: What shall i do, reinstall the terminal?:(

---

### Post by Manny C on 2005-10-20
[quote=Mathias-K]Thanks, but as i wrote in the other reply, my Terminal is getting screwy on me. I cannot write anything, when i'm prompted for the password!:confused: What shall i do, reinstall the terminal?:([/quote]

Read my next post in reply to your 2nd last post! ;)

---

### Post by BoyOfDestiny on 2005-10-20
You don't have to use terminal! It's for the people that want it, know how to use it, and understand why it is there.

Go to System->Administration->Synaptic Package manager

It is a nice gui app, you can check what repos are enabled, update, install, remove applications, etc. 

Hope all your repos are enabled, if not post again and we'll help!

---

### Post by Jenda on 2005-10-20
Mathias K:
1. If you do not like bash, use Synaptic (System > Administration > Synaptic Package Manager). It's a GUI frontend for apt-get. I prefer and recommend the terminal.
2. You CAN type your password, it's just not displayed. Type your pwd and press enter you'll see. Manny C explains this a few posts up.
3. No matter what media player you use, you will need the codecs. Many places explain how to do this, but I will repeat it just for you. First put this in the terminal to open sources.list.
```
sudo gedit /etc/apt/sources.list
```
Enter your password (you know you can...) and insert the following line at the end of the file:
```
deb ftp://ftp.nerim.net/debian-marillat/ etch main
```
save & exit
Note that the next step is a lot of downloading. 50MB+
```
sudo apt-get update
sudo apt-get install w32codecs libdivx4linux
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg lame sox ffmpeg mjpegtools vorbis-tools
gst-register-0.8
sudo gedit /etc/apt/sources.list
```
The last command opens the text editor again, and YOU ABSOLUTELY MUST REMOVE THE LINE YOU ADDED EARLIER!!!!
save & exit
That should be it. I hope I didn't leave anything out.
4. For movies, you should choose between xine and totem-xine - I prefer xine
```
sudo apt-get install xine-ui
```
All set. You might wanna associate xine with the formats.
```

sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
```

---

### Post by Jenda on 2005-10-20
I didn't include DVD playback. You can use the old [Ubuntu Starter Guide](http://ubuntuguide.org) for this. It's where I got all my info from.

---

### Post by patrick295767 on 2005-10-20
[QUOTE=Mathias-K]I must say that if i ever thought that parts of Windows were ilogic, DOS-like and unnessecarily complex, then Linux has made me forget all that!

When i copy paste your code into the terminal, i get the followong error:

[I]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/I]

Aha, i thought, i'll just write "sudo" in front of it and then type my password. What happens then? I'm prompted for the password, but then i'm unable to type it.. Well...:confused: 

The developers of Linux seem brilliant, so why don't they just abandon this dusty DOS-mania and make it all automatic in the package manager or as a .tar-installer?

Regards, Mathias[/QUOTE]
  
  
  
I got also same problem at beginning... 
Just type : 
su
enter ur root password 
   
then ur $ will be a #
then, u wont have problem anymore with permissions ... 
  
type all your : 
# apt-get update
# apt-get install mplayer banshee
# apt-get -f install

Good courage & let us know about ur progress and resutls ! 

Pat'

---

### Post by trash on 2005-10-20
check out the Easy Ubuntu forums [http://ubuntuforums.org/forumdisplay.php?f=86](http://ubuntuforums.org/forumdisplay.php?f=86), there are no less than three scripts that make it dead easy for anybody to get everything they need installed ... Automatix, easyubuntu and DEIUCbuntu

automatix
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

easy ubuntu
[http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629)

DEIUCbuntu
[http://www.jpoa.ecwhost.com/](http://www.jpoa.ecwhost.com/)

---

### Post by Mathias-K on 2005-10-20
[QUOTE=Jenda]Mathias K:
Note that the next step is a lot of downloading. 50MB+
```
sudo apt-get update
sudo apt-get install w32codecs libdivx4linux
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg lame sox ffmpeg mjpegtools vorbis-tools
gst-register-0.8
sudo gedit /etc/apt/sources.list
```
The last command opens the text editor again...[/QUOTE]

Thank you very much for this help. I must admit that i got a bit frustrated over errors that i as a reasonably experienced PC-user understood nothing of..

Well, i insert the line of text, saves the document, and then paste the code above and run it. But i don't think it works. It asks me:

[SIZE="1"][I]Need to get 9774kB/10.2MB of archives.
After unpacking 26.2MB of additional disk space will be used.
Do you want to continue [Y/n]?[/I]
[/SIZE]

And if i type "y" og "Y" or even my password, it just writes "Abort." like if i typed "n". How do i do this?:confused:

---

### Post by Jenda on 2005-10-20
Hmmm. I'm not sure, but i know for a fact that a simple "enter" should do the trick when the choice is [Y/n] (the capital letter is default). Try that and if it still aborts, please post the abort message here. Someone is bound to know what that means.
Edit: And paste each line of code separately. I don't know exactly what happens if you dont. And one more thing. DO NOT upgrade your system (sudo apt-get upgrade) with that extra line in your sources.list. That WILL bust a cap in yo' PC's ar*e.

---

