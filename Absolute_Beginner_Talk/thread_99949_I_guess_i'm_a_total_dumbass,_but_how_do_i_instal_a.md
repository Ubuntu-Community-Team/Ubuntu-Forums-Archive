---
title: "I guess i'm a total dumbass, but how do i instal a program?"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by zwcp on 2005-12-06
Ive downloaded the new firefox 1.5 to my desktop, but how do I install it? ive tried using synaptic, but i dont really know what i'm doing...


Help anybody?

---

### Post by moberry on 2005-12-06
Synaptic is the best way. I cam from debian so I cannot get out of the habit of using apt-get, and apt-cache. Did you get firefox from the mozilla website? If so just de-compress it into your /usr/local like this

sudo tar -zxf file_name.tar.gz -C/usr/local/bin
 make sure all the files are in /usr/local/bin/ and not /usr/local/bin/firefox

to use apt... sudo apt-get install mozilla-firefox

---

### Post by sethmahoney on 2005-12-06
[QUOTE=zwcp]Ive downloaded the new firefox 1.5 to my desktop, but how do I install it? ive tried using synaptic, but i dont really know what i'm doing...


Help anybody?[/QUOTE]

Synaptic is always the best way to go for installing new software, but if what you want isn't in the repositories, there are two newbie-friendly options:
1.  For some software (firefox 1.5 has one, I know) there are install scripts floating around the Ubuntu forums.  Do a search for it - it even comes with instructions.
2.  If there isn't a script, and there is a .deb file you can download, download it and, in the terminal, type

sudo dpkg -i filename.deb

Only replace 'filename' with the name of the file.

---

### Post by aysiu on 2005-12-06
My advice? Use 1.0.7 until you're more familiar with things.

When you're confident enough to venture out to installing things not in the repositories, then follow [these instructions](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by zwcp on 2005-12-06
[QUOTE=moberry]Synaptic is the best way. I cam from debian so I cannot get out of the habit of using apt-get, and apt-cache. Did you get firefox from the mozilla website? If so just de-compress it into your /usr/local like this

sudo tar -zxf file_name.tar.gz -C/usr/local/bin
 make sure all the files are in /usr/local/bin/ and not /usr/local/bin/firefox

to use apt... sudo apt-get install mozilla-firefox[/QUOTE]

okay... im a little lost here... i downloaded the firefox file from the official website an i now have a folder on my desktop called:

firefox-1.5.tar.gz


Tell me again what to do... preferably as a piece of code i can just copy paste into my terminal...

---

### Post by aysiu on 2005-12-06
[QUOTE=zwcp]okay... im a little lost here... i downloaded the firefox file from the official website an i now have a folder on my desktop called:

firefox-1.5.tar.gz


Tell me again what to do... preferably as a piece of code i can just copy paste into my terminal...[/QUOTE] See--that's what I was trying to tell you before. If it's a .tar.gz, it's not as simple as copying and pasting one command into a terminal. You'll have to follow all the steps outlined in the link I linked to above.

I would advise that you stick with 1.0.7 until you're more comfortable with Ubuntu.

---

### Post by zwcp on 2005-12-06
[QUOTE=aysiu]My advice? Use 1.0.7 until you're more familiar with things.

When you're confident enough to venture out to installing things not in the repositories, then follow [these instructions](https://wiki.ubuntu.com/FirefoxNewVersion)[/QUOTE]


checked out the link you told me to..... okay  I get the picture :D .... i'll wait till I get a little more experienced ;)

---

### Post by Estariel on 2005-12-06
Yesterday someone asked a similar question, and a wrote a rather lengthy reply on the possible installation methods...
check it out i you want to
[http://www.ubuntuforums.org/showthread.php?t=99536](http://www.ubuntuforums.org/showthread.php?t=99536)

it is reply #7.

---

