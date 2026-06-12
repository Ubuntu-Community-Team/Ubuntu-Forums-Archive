---
title: "Youtube"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by jwkungfu on 2008-02-28
Hello,
I'm having problems watching videos on YouTube.
While my Dell Laptop PC is trying to download the video my screen dimms out but then comes back to life after a minute or two...
Another problem is that the control buttons on the YouTube video player seem to be crunched up together and therefor unusable...
Any advice please?
John

---

### Post by kesman on 2008-02-28
what browser are you using and how did you install flash player into it?

---

### Post by karthikbalaji on 2008-02-28
I also had similar problems after installing ubuntu. Firefox detected the missing codec and installed it. Even after that I was not able to watch videos. I manually downloaded the flash player from the following link and installed it. It worked . Try it ...

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

---

### Post by jwkungfu on 2008-02-28
I'm using Mozilla FireFox.
I usually select VLC media player when I view DVD's....?

---

### Post by jwkungfu on 2008-02-28
OK, I'll give that a crack... cheers!!

---

### Post by jwkungfu on 2008-02-28
> **karthikbalaji said:**
> I also had similar problems after installing ubuntu. Firefox detected the missing codec and installed it. Even after that I was not able to watch videos. I manually downloaded the flash player from the following link and installed it. It worked . Try it ...

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

OK, I clicked on the link, my PC has downloaded a file, I click on that, something opens up.... then what???

---

### Post by deepclutch on 2008-02-28
^extract that archive u downloaded with fileroller.then copy "libflashplayer.so" into ur /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins directory.make sure u downloaded latest flash9 for Linux. :)

and u need to be root for moving libflashplayer.so into /usr/** directories.for that u can do as following:
press ALT+F2 and inside run : 
```
 gksudo nautilus  
```
now nautilus file manager as root opens.copy libflashplayer.so from ur  /home/user/xx wherever u extracted the file to the /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins/ directories.that's it! :)

---

### Post by karthikbalaji on 2008-02-28
Simply way is extract the tar ball.

goto the extracted directory thru terminal and run the install script there as root ..

kb@Gutsy:~/install_flash_player_9_linux$ ./flashplayer-installer 

It ll take care of the formalities ...

---

### Post by jwkungfu on 2008-02-28
> **deepclutch said:**
> ^extract that archive u downloaded with fileroller.then copy "libflashplayer.so" into ur /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins directory.make sure u downloaded latest flash9 for Linux. :)

and u need to be root for moving libflashplayer.so into /usr/** directories.for that u can do as following:
press ALT+F2 and inside run : 
```
 gksudo nautilus  
```
now nautilus file manager as root opens.copy libflashplayer.so from ur  /home/user/xx wherever u extracted the file to the /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins/ directories.that's it! :)

OK, did the gksudo nautilus thingy in a terminal window...
Entered my password and something seemed to happen...
Went back and clicked on OPEN in the Downloads window...
ZIP...
???

btw. what is fileroller? where are plugins located? what is nautilus file manager? is it better or worse than the standard file manager that comes with Ubuntu?

---

### Post by jwkungfu on 2008-02-28
> **karthikbalaji said:**
> Simply way is extract the tar ball.

goto the extracted directory thru terminal and run the install script there as root ..

kb@Gutsy:~/install_flash_player_9_linux$ ./flashplayer-installer 

It ll take care of the formalities ...

opened a terminal window... copied and pasted...

~/install_flash_player_9_linux$ ./flashplayer-installer

result= 

bash: /home/john/install_flash_player_9_linux$: No such file or directory
john@john-laptop:~$

---

### Post by constrictor on 2008-02-28
Did you extract the tar file before going to the terminal to install the flash player? You should right click on the tar ball and say extract here. Once that is done go to your terminal and cd into the folder that the extraction process creates eg "install_flash_player" or something like that. Once you have done that run 

chmod +x install_flashplayer
sudo ./install_flashplayer

that should install it to your brower.

---

### Post by jwkungfu on 2008-02-29
I am new to linux and new to ubuntu
I havn't installed any players?

---

### Post by jwkungfu on 2008-02-29
Sorry but I made this post on Absolute Beginner Talk because that is just exactly what I am.... I don't understand your reply could you break it down in plain English for me?
thanks

---

### Post by constrictor on 2008-02-29
Sorry i was not clear earlier. Sometimes the flash player that ubuntu downloads and installs does not work really well, and you have to download it from adobe or macromedia (so to speak). As i gather you have done that already and don't know what to do with the file you have which should have the extension "tar.gz".

Basically adobe have put this together so that it can install it for you by itself, all you need to do is to unpack the file and run it. here's how...
I got these instructions from the adobe site.

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

here is how to navigate to the directory

```
cd install_flash_player_9_linux
```

and type in after that

```
./flashplayer-installer
```

   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by jwkungfu on 2008-02-29
Many thanks!!  :O)
I have the file on my desk top
Open a terminal and typed the instruction you advised

bash: cd: install_flash_player_9_linux: No such file or directory


?????????????

---

### Post by constrictor on 2008-02-29
if it's on your desktop then the file should read

```
cd Desktop/install_flash_player_9_linux
```

pay attention to the capital "D" in Desktop.

---

### Post by Myglaren on 2008-02-29
You need to navigate to wherever the file is, in this case the desktop.

Open the terminal.
type CD Desktop  Enter
Type DIR Enter to see that you are in the desktop and that the files and folders you need are there,  

Issue the command:  ./flashplayer-installer

Bob's your mother's brother.

---

### Post by jwkungfu on 2008-03-01
Many many thanks to all those that have replied to my post!!!!!!!!!!!!!!!!

I think I have fixed the problem!!!!!!!!!!

I am looking at a YouTube Video and it seems to be downloading properly (without the dim outs) and the control buttons are back to where they are meant to be!!!   :O)

Not 100% sure exactly how I did it.....
I kept extracting the file I downloaded from Adobe on to my desktop until there appeared to be a file/application there that said Flash Installer...
I followed the tip about making sure I was on the desktop... and the terminal command that I was told to try seemed to kick start some activity, which I kept typing Yes to and it said that it was downloaded!!!

Now... how to I mark this thread as solved/finished?

:guitar:

---

### Post by constrictor on 2008-03-01
glad i could help...:popcorn:

---

