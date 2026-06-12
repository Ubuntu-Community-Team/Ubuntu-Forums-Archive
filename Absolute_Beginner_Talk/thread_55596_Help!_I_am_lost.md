---
title: "Help! I am lost"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by kairos911 on 2005-08-09
When it comes to Linux/Ubuntu rookies I think I rise to the top of the list.  I am trying to install a program.  I understand that I must configure the program.  I have read the Install and Read Me files.  I am told that a "typical" setup is performed by typing the following command:  make install.config

But, I don't even know where it is I am supposed to type that command.

Thanks in advance for an answer.  Please though, don't send me back to Windows.  I like it here better.  I am determined to learn this.

---

### Post by schultzy on 2005-08-09
I'm certainly no linux guru. But I do believe that you need to open Terminal and type the commands in there. You may also want to see if there is a repository for the application you are trying to install. Take it from me, it's much easier...

Good luck!

---

### Post by krusbjorn on 2005-08-09
Yeah, open a terminal and make your way to the directory containing the file in question (using the "cd" command). then enter the commands specified in the readme file..

---

### Post by kairos911 on 2005-08-09
[QUOTE=krusbjorn]Yeah, open a terminal and make your way to the directory containing the file in question (using the "cd" command). then enter the commands specified in the readme file..[/QUOTE]
 I'm almost embarassed enough to go back to Windows!  There is something very simple that I'm missing.  I was unable to install the original program I was working with.  So, I went to RealPlayer.  I thought that I could start with something that might actually come prepared and ready for installation.

But, I'm still missing something.  I go to terminal.  I can even cd to the directory into which I extracted the original file.  But, none of the commands in my "Install" instructions work.

On a different note, I downloaded RealPlayer for Linux.  It came as a .bin file.  Ubuntu told me that I needed to convert the file to an executable file.  RealPlayer gave instructions on how to convert.  However, like before, the terminal gives me error messages each time I try.

Any help you can provide to guide me is much appreciated (in advance).

Thanks!

---

### Post by TristanMike on 2005-08-09
Hi, I'm an Uber-Rookie too.  :smile:  
First and foremost, Real Player is available throught the repositories and apt-get/synaptic. So you can either search synaptic for Real Player or you can install it via apt-get
```
sudo apt-get install realplayer
```, the choice is yours.

But you must enable the repositories and all of that other glorious stuff found @ [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories).

---

### Post by krusbjorn on 2005-08-09
[QUOTE=kairos911]I'm almost embarassed enough to go back to Windows!  There is something very simple that I'm missing.  I was unable to install the original program I was working with.  So, I went to RealPlayer.  I thought that I could start with something that might actually come prepared and ready for installation.

But, I'm still missing something.  I go to terminal.  I can even cd to the directory into which I extracted the original file.  But, none of the commands in my "Install" instructions work.

On a different note, I downloaded RealPlayer for Linux.  It came as a .bin file.  Ubuntu told me that I needed to convert the file to an executable file.  RealPlayer gave instructions on how to convert.  However, like before, the terminal gives me error messages each time I try.

Any help you can provide to guide me is much appreciated (in advance).

Thanks![/QUOTE]

Hey, dont be embarassed, and for Gods sake, dont go back to windows!

Instead, go to [www.ubuntuguide.org](www.ubuntuguide.org). It's an incredible place. There are other media players that are at least as good as realplayer available for you, within a few clicks ;)

Edit: By the way, when you ask for help, and actually have some error messages, *always* copy/paste them into your post. It's a lot easier to help if we know what's wrong ;)

---

### Post by tonysathre on 2005-08-10
here this will help....everyone needs to know how to compile apps so remember this...

make a diirectory (probably in your home directory) for the new app... move the gzipped tarball to that directory. open a terminal and [FONT=Courier New]cd[/FONT] (change directory) to the directory containing you tarball. type [FONT=Courier New]tar zxvf filename.tar.gz[/FONT] for a gzipped tarball or type [FONT=Courier New]tar jxvf [/FONT] for a bzipped tarball. this will extract all the files..then [FONT=Courier New]ls[/FONT] to see the new subdirectory that was created..then [FONT=Courier New]cd[/FONT] to that directory..now type ./configure then type [FONT=Courier New]make[/FONT] then [FONT=Courier New]sudo make install[/FONT]...thats it...after doing a couple of times you should be able to compile apps in now time...just the time that it takes to make and make install of course.

---

