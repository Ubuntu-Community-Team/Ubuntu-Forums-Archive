---
title: "myspace"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by ghoran on 2007-12-18
When my daughter comes into her myspace page it is supposed to play music.

Instead it says:

"Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Click here to get the latest flash player."

When she choose click here it lists a tar.gz, an rpm or a yum(?)

I believe I took the latest flash from Synaptic Package Manager.
I attached the information from Synaptic Package Manager.

---

### Post by siciliancasanova on 2007-12-18
Download the tar.gz file and install

---

### Post by daimaru on 2007-12-18
well it seems that you have flash-nonfree installed so this is kinda weird. 
could you post the link to the site so we can check if it shows the same error?

only other thing i can think of is reinstalling flash player.

---

### Post by Presto123 on 2007-12-18
Just click on the "Get Adobe Flash" when it lists the error.

Install the .tar.gz file, extract it to your desktop and do this in terminal:

```
cd Desktop/install_flash_player_9_linux
```

That will get you to the file where you need to be. Then use this code:

```
./flashplayer-installer
```

And follow the prompt.

After this is over, you can get rid of the folder and the download, unless you want it for the future. (It doesn't have to stay on your desktop after installation.)

---

### Post by ghoran on 2007-12-18
Thanks so much.

I do have a few comments.
Sorry, but I figured since I just stepped through it I could give comments.

I use UNIX at work so I am familiar with tar.gz files.
If you open the file with Archive manager and extract it the tar.gz file it is still a tar file
I do not have the machines to go in as root so I need to sudo to do things

Should the how to also contain

1. Save the tar.gz file to disk (usually to your desktop). The download dialog box will note where it dropped the file. At the bottom on the dialog it will say All files downloaded to ****.
2. Open a terminal (Applications -> Accessories -> Terminal)
3. cd to where you saved the file (usually to Desktop)
    cd Desktop   <- Note: Capitol D
4. type ls and hit enter. You should see a file names something like install_flash_player_9_linux.tar.gz
5. You need to unzip(gunzip) and extract(tar) this file
5a. unzip the file
     Type: gunzip install_flash_player_9_linux.tar.gz
     After hitting enter you should have a file called : install_flash_player_9_linux.tar
     This is a smaller file as the point of gzip/gunzip is compress/decompress file
5b. extract the files within the tar file
     Type: tar -xvf install_flash_player_9_linux.tar
     This will create a directory of files. The point of tar is to gather several files and directories into a single file. The xvf options extract (x) the files.
6. Move into the directory you just created
    cd install_flash_player_9_linux
7. Run the installation program as root. If you do not prepend the installation with sudo you will run it under the current user. If the current user is not the root user then the other users of this computer will not get the flashplayer.
    sudo ./flashplayer-installer
8. After the installation is complete you can remove this entire folder and the tar file.

---

### Post by spiderbatdad on 2007-12-18
flashplayer-nonfree in synaptic works fine for me

---

### Post by spiderbatdad on 2007-12-18
the thumbnail in your original post only shows the adobe plugin of flashplayer, not the actual flashplayer```
sudo apt-get install flashplayer-nonfree
```or go to synaptic

---

### Post by ghoran on 2007-12-18
I did it to work by taking down the tar ball and extracting.
One thing to add to the how to is:

To the question:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

You need to type /usr/lib/firefox

On my other computer I tried
sudo apt-get install flashplayer-nonfree

and I got an error that said that 
E Couldn't find package flashplayer-nonfree

---

### Post by spiderbatdad on 2007-12-18
hmmm. sorry. I guess it is called flashplugin-nonfree

---

### Post by Presto123 on 2007-12-18
> **ghoran said:**
> Thanks so much.

I do have a few comments.
Sorry, but I figured since I just stepped through it I could give comments.

I use UNIX at work so I am familiar with tar.gz files.
If you open the file with Archive manager and extract it the tar.gz file it is still a tar file
I do not have the machines to go in as root so I need to sudo to do things

Should the how to also contain

1. Save the tar.gz file to disk (usually to your desktop). The download dialog box will note where it dropped the file. At the bottom on the dialog it will say All files downloaded to ****.
2. Open a terminal (Applications -> Accessories -> Terminal)
3. cd to where you saved the file (usually to Desktop)
    cd Desktop   <- Note: Capitol D
4. type ls and hit enter. You should see a file names something like install_flash_player_9_linux.tar.gz
5. You need to unzip(gunzip) and extract(tar) this file
5a. unzip the file
     Type: gunzip install_flash_player_9_linux.tar.gz
     After hitting enter you should have a file called : install_flash_player_9_linux.tar
     This is a smaller file as the point of gzip/gunzip is compress/decompress file
5b. extract the files within the tar file
     Type: tar -xvf install_flash_player_9_linux.tar
     This will create a directory of files. The point of tar is to gather several files and directories into a single file. The xvf options extract (x) the files.
6. Move into the directory you just created
    cd install_flash_player_9_linux
7. Run the installation program as root. If you do not prepend the installation with sudo you will run it under the current user. If the current user is not the root user then the other users of this computer will not get the flashplayer.
    sudo ./flashplayer-installer
8. After the installation is complete you can remove this entire folder and the tar file.

Honestly...this looks like going around the butt to get to the elbow, and I was shooting for the simple way of doing it. Yeah, it only extracts to the current user, sorry about that, but I'm sure you can just simplify things by making it available to all users. 

Let me see...

---

### Post by Presto123 on 2007-12-18
Here we go...After I installed it a while back, it installed the file on my nephew's login as well. I didn't have to go through the trouble of going into terminal.

I just logged out and opened MySpace under his login and had no problems.

But, if you are still having problems, then most certainly use your method.

---

### Post by bw44 on 2007-12-18
> **ghoran said:**
> I did it to work by taking down the tar ball and extracting.
One thing to add to the how to is:

To the question:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

You need to type /usr/lib/firefox

On my other computer I tried
sudo apt-get install flashplayer-nonfree

and I got an error that said that 
E Couldn't find package flashplayer-nonfree

Have a look at a utility which user mdpalow has been developing: 

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

I've used it mostly for the backup/recovery features, but other users have sung its praises for getting their DVD/Video streaming stuff to work, including flash-player.  See Option 3 on the menu.

Obviously, your mileage may vary, but it's worth a try.

Cheers, and good luck!

---

