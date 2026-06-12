---
title: "Opera 9"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-05-01
Hi all! I have Opera 9( beta )on my desktop.It is a .deb ext. Each time I try to install I get a 'No file or directory found'. Can anyone point me in the right direction?
Thanks

---

### Post by angkor on 2006-05-01
How are you trying to install it?

A .deb can usually be installed by entering:

```
sudo dpkg -i yourpackage.deb
```

in the terminal.

In Dapper (the next ubuntu release) you're able to double-click .debs to install them.

---

### Post by Sbarton on 2006-05-02
[QUOTE=angkor]How are you trying to install it?

A .deb can usually be installed by entering:

```
sudo dpkg -i yourpackage.deb
```

in the terminal.

In Dapper (the next ubuntu release) you're able to double-click .debs to install them.[/QUOTE]

Sorry about delay in getting back!

I have installed Opera before as you described but this time it just is not installing . There is a 'error processing- no file or directory found' reponse. I'ts there on the Desktop though?
Pleased to here installing .deb files will be easier in Dapper.
regards

---

### Post by byenary on 2006-05-02
One should not have their files on the desktop, try placing the file in you home folder and than position yourself in the terminal in the /home folder and do the dpkg

---

### Post by Engnome on 2006-05-02
Try adding quation marks ("") around the search path. A space will be taken as: here comes something else by bash. Happens to me sometimes when i drag and drop stuff into terminal.

---

### Post by fastguy on 2006-05-02
I'm using the latest builds from The Desktop Team:

[http://my.opera.com/desktopteam/blog/show.dml/241846](http://my.opera.com/desktopteam/blog/show.dml/241846)

Download the specific static dapper package.

then dpkg -i path_to_package

Should do the trick....

Fast

---

### Post by catlett on 2006-05-02
I just did it for the heck of it (I don't use opera too much, firefox extensions got me hooked but I figured I'd check the beta out)
Anyways I followed your link. Clicked on Unix. Clicked on Intel-Linux. Clicked on the deb package with dapper in it.
Downloaded it to my desktop. Opened my home folder. Dragged the deb package to my home folder. Opened the terminal. Typed  sudo dpkg -i opera(physically press the tab key. It will finish the name of the package. This package has a long name and there's no need to type it in, the terminal will fill it in when you hit "tab"). It asks for my password. I entered my password and it ran the install.
I had opera installed already. So it chose this new one. The launcher in my menu now launches this one.
It should put opera in your menu even if you didn't have it. If it doesn't show up, open the terminal and type "update-menus" this will refresh your menu and opera should be there.
Just thought I'd give the run down in case someone new was interested but didn't know deb.s yet.

---

### Post by nanotube on 2006-05-02
[QUOTE=Sbarton]Sorry about delay in getting back!

I have installed Opera before as you described but this time it just is not installing . There is a 'error processing- no file or directory found' reponse. I'ts there on the Desktop though?
Pleased to here installing .deb files will be easier in Dapper.
regards[/QUOTE]
if it's on the desktop, then you have to go to the Desktop directory, and THEN run the dpkg stuff. so you would open a terminal, and then do
```
cd Desktop
sudo dpkg -i opera_blablabla.deb
```

---

### Post by catlett on 2006-05-02
I'm so dumb I always tried cd /home/catlett/Desktop and I would get no file or directory. I stopped trying to get there and just drag stuff into home. Thanks for the insight.
Why is that? Is it because I'm in /home/catlett already and it is a given? That it only needs a directive from /home/catlett i.e. desktop?

---

### Post by nanotube on 2006-05-02
[QUOTE=catlett]I'm so dumb I always tried cd /home/catlett/Desktop and I would get no file or directory. I stopped trying to get there and just drag stuff into home. Thanks for the insight.
Why is that? Is it because I'm in /home/catlett already and it is a given? That it only needs a directive from /home/catlett i.e. desktop?[/QUOTE]
hmm, well, maybe you forgot to capitalize Desktop? because cd /home/catlett/Desktop should work just as well as cd Desktop. try letting the tab completion work for you. so when typing your command, try "cd /hom<tab> cat<tab> Des<tab>" - that lets you avoid misspellings. :)

and of course, if you want to know more in general about commandline, check the tutorials listed in my sig under "other command line resources" section.

---

### Post by catlett on 2006-05-02
Like I said I'm going to follow you around. 
I did the tab scenario you laid out and I got to Desktop! I must have done it a dozen times earlier to make sure and it didn't work. It must have been misspelling like you guessed. Well thanks again for the enlightenment.

---

### Post by nanotube on 2006-05-02
[QUOTE=catlett]Like I said I'm going to follow you around. 
I did the tab scenario you laid out and I got to Desktop! I must have done it a dozen times earlier to make sure and it didn't work. It must have been misspelling like you guessed. Well thanks again for the enlightenment.[/QUOTE]
hehe you're welcome. have fun. :)

---

### Post by mrgnash on 2006-05-02
The fonts under Dapper are still fugly, I'm sorry to see :(

Opera is my fave browser but I haven't used it in awhile for this very reason.

---

### Post by nanotube on 2006-05-03
[QUOTE=mrgnash]The fonts under Dapper are still fugly, I'm sorry to see :(

Opera is my fave browser but I haven't used it in awhile for this very reason.[/QUOTE]
tried installing the *msttcorefonts* package?

---

### Post by mrgnash on 2006-05-03
Yep, and my fonts are fine in every other application.

---

### Post by nanotube on 2006-05-03
[QUOTE=mrgnash]Yep, and my fonts are fine in every other application.[/QUOTE]
hmm interesting. :) 
i dont use opera myself, so don't know what else to suggest...

---

### Post by Sbarton on 2006-05-03
Hi folks! Thanks for all the input!  nanotube that's how I installed before but stupidly I was typing cd in 'Capitals'. ](*,) 
Thanks again
Regards to all.

---

### Post by nanotube on 2006-05-03
[QUOTE=Sbarton]Hi folks! Thanks for all the input!  nanotube that's how I installed before but stupidly I was typing cd in 'Capitals'. ](*,) 
Thanks again
Regards to all.[/QUOTE]
Heh yea, always gotta watch out for case-sensitivity in linux. it's a frequent mistake, so don't feel bad about it. :)

---

