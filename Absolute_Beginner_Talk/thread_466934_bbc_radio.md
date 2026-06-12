---
title: "bbc radio"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Noyminibin on 2007-06-07
How do i get the bbc radio to play in the web browser at the minute

i went here [http://www.real.com/linux/](http://www.real.com/linux/) and downloaded the file but i get a .bin file how do i install it ?

---

### Post by Outrunner on 2007-06-07
```
/home/username/Desktop/filename.bin
```

[http://monkeyblog.org/ubuntu/installing/#installer](http://monkeyblog.org/ubuntu/installing/#installer)

---

### Post by Noyminibin on 2007-06-07
craig@craig-desktop:~$ /home/craig/Desktop/RealPlayer10GOLD.bin
bash: /home/craig/Desktop/RealPlayer10GOLD.bin: Permission denied

Thats what i got if i did the right thing ?

---

### Post by Outrunner on 2007-06-07
```
sudo chmod 755 /home/craig/Desktop/RealPlayer10GOLD.bin
```

Should give you permission.

---

### Post by Noyminibin on 2007-06-07
craig@craig-desktop:~$ sudo chmod 755 /home/craig/Desktop/RealPlayer10GOLD.bin
Password:
craig@craig-desktop:~$ 

I entered my password and then that bottom line came up how do i know if it worked ?

---

### Post by Noyminibin on 2007-06-07
dnt matter i got it know hopefully

---

### Post by Noyminibin on 2007-06-07
I now get "Could not find an appropriate hxplay or realplay in the system path to use as an embedded player

---

### Post by thedarky on 2007-06-07
> **Noyminibin said:**
> craig@craig-desktop:~$ /home/craig/Desktop/RealPlayer10GOLD.bin
bash: /home/craig/Desktop/RealPlayer10GOLD.bin: Permission denied

Thats what i got if i did the right thing ?

Hi, I'm on the same track doing a manual install of the REalplayer bin installer and I've hit the same permissions problem, so can I ask for code help here too please?

I'm working in my Desktop directory, have found and added needed dependent package - now have got as far as running the installer and it has asked for a directory for the install

as directed by the official documentation, I gave the directory as /opt/RealPlayer.
The installer said
> Copying RealPlayer files...Error creating directory /opt/RealPlayer (Permission denied), exiting...
Cleaning up installation files...
Done.

I feel sure that I am not understanding the syntax, so any help with changing directories etc will be really appreciated.

---

### Post by Songwind on 2007-06-07
Looks like the installer tries to do a system-wide (as opposed to user specific) install, so you have to run it via **sudo**.  Basic user rights don't extend to modifying the /opt directory structure.

I am using mplayer and the mplayer plugin for this, so I can't say, but maybe someone else here can - is there no repository package for the RealPlayer code?

---

### Post by tgalati4 on 2007-06-07
Try installing by putting in  your home directory.  Does /opt directory exist?  Does it have user or root permissions?

---

### Post by thedarky on 2007-06-07
> **Songwind said:**
> Looks like the installer tries to do a system-wide (as opposed to user specific) install, so you have to run it via **sudo**.  Basic user rights don't extend to modifying the /opt directory structure.

I am using mplayer and the mplayer plugin for this, so I can't say, but maybe someone else here can - is there no repository package for the RealPlayer code?

Hi,  bearing in  mind that I am an absolute newbie, both to linux and desktops, I've battled away through doing this single manual install because I really need Realplayer for streaming radio in a ppc install - - I came here for the linux commands because there's not many around in the ppc forum and I'd like to get this done because I'm getting so near - - -.
So, there is no supported ppc RealPlayer installation right now and I've spent 3 days chasing this one down, to answer your second question.

Any way    helppp!   sudo got us rolling thanks so much but now the installer want me to 
> enter the prefix for symbolic links
and it's tapping it's fingers  impatiently

---

### Post by Noyminibin on 2007-06-07
> **tgalati4 said:**
> Try installing by putting in  your home directory.  Does /opt directory exist?  Does it have user or root permissions?

ehh i only installed ubuntu yesterday

---

### Post by thedarky on 2007-06-07
Hi,

Success!
I stopped panicking,  reread the official install instructions and let the configuration go through as default.

Thanks for the code advice.  I now have Firefox handling the streaming files effortlessly.

cheers.

---

### Post by Noyminibin on 2007-06-07
so what did you do after you installed real player to get it to work ?

---

### Post by Noyminibin on 2007-06-07
and now i have lost all sound ?

---

### Post by Noyminibin on 2007-06-07
ok now just no sound in real player ?

---

### Post by Noyminibin on 2007-06-07
516 people viewing this foum and no one can tell me why i get  	I now get 
"Could not find an appropriate hxplay or realplay in the system path to use as an embedded player"

Or why i am no longer getting sound in real player

---

### Post by tgalati4 on 2007-06-08
What is your exact hardware configuration?

I normally download BBC podcasts and listen to them as mp3 files.  I don't bother with streaming. 

If you want to lift the visibility of your post, you need to issue a 

bump

in the thread to raise it as an offering to the Ubuntu Gods.

---

### Post by neo.patrix on 2007-06-08
It is pretty simple to install,

try ,

```
sudo bash /home/craig/Desktop/RealPlayer10GOLD.bin
```

It should work, also try same thing for that other .bin file

---

### Post by Michaelt74 on 2007-06-08
I downloaded the Linux version to my desktop and typed 'cd Desktop' and followed the following link
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

Make sure you have the media player connectivity plugin for Firefox
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Run the wizard and configure Real player streams accordingly

---

