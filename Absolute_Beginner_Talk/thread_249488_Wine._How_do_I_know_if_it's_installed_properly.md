---
title: "Wine. How do I know if it's installed properly ?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-02
A night or so ago, I decided to install Wine, so that I could use DVD Shrink. First thing to know I guess, is that I'm using the repositories which are standard to the Automatix installer program. So I guess that means I have everything available under the sun, right ? 

I opened synaptic and searched for "wine", but nothing came up. So I just looked for it, and it was there, which is strange, isn't it ? Why would it not come up in the search ? Anyway, I opted to install it, and everything I guess went fine. Should I however, be able to see Wine listed in one of my menus somwehre ? Because, I don't see it. 

It's listed as version 0.9.9 -0ubuntu2" in the repository list.   

Now for part deux. 

I only installed Wine so that I could use DVD Shrink. I went to WineHq and found the app page. But when I click on the download link, it takes me to a strange page, which then re-directs to another page which is totally unrelated to dvd shrink. They both are actually, IMO. 
But when I right click and save the link, it's saved as a .zip file. When I choose to open it, I get:

> The filename "dvdshrink32setup.zip" indicates that this file is of type "ZIP archive". The contents of the file indicate that the file is of type "HTML document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.  
I guess it's because it's not a .gz file, but then..how am I supposed to operate this ?

Basically, I just want to know how to install DVD shrink. On a side note, do I have to install wine tools ? I'd rather not, if it's not necessary, but I'll take the word of someone who knows. So please, any help would be greatly appreciated. 

Doug

---

### Post by reacocard on 2006-09-02
Wine doesn't create a menu entry for itself, beacuse it doesn't really have a GUI. to see if its installed properly, open a terminal and type
```
winecfg
```
that will open wine's configuration dialog. take a moment and go to the devices tab and tell it to autodetect. exit winecfg. Once you find dvdshrink, run the installer with
```
wine /path/to/setup.exe
```

EDIT: here's a spot to download it: [http://www.softpedia.com/progDownload/DVD-Shrink-Download-4128.html](http://www.softpedia.com/progDownload/DVD-Shrink-Download-4128.html)
You'll have to use the RO mirror, the US one is down.

---

### Post by cyberlite on 2006-09-02
Hi try here
[http://kubuntu101.blogspot.com/2005/10/installing-wine.html](http://kubuntu101.blogspot.com/2005/10/installing-wine.html)
:-\"

---

### Post by Sweet Spot on 2006-09-02
Ok, ran winecfg, and autodetected. That went fine. When I tried to look at the audio tab, got some errors concerning drivers, which opened another dialogue, and I clicked on ALSA as well as OSS , but don't think that resolved the issue. 

Question about this: > wine /path/to/setup.exe  Am I meant to put in the location of where Wine is ? It's on my desktop, so should it be wine/desktop/to/setup.exe ?  or does it have to be more specific or anything else ? Sorry, I'm a dope w/this stuff. I ran it as was typed and got a message saying not found etc.. Hence the questions. Thanks again. 

Doug

---

### Post by reacocard on 2006-09-02
no, something like
```
wine /home/aren/desktop/dvdshrink32setup.exe
```
it's the path to the installer executable. if there are any spaces in the path, put in quotes, like so:
```
wine "/home/aren/desktop/my downloads/dvdshrink32setup.exe"
```

to make it easy, just drag the executable into the terminal and its path will be entered automatically.

---

### Post by Sweet Spot on 2006-09-02
> **cyberlite said:**
> Hi try here
[http://kubuntu101.blogspot.com/2005/10/installing-wine.html](http://kubuntu101.blogspot.com/2005/10/installing-wine.html)
:-\"

I think this only applies to Kubuntu. I did try and follow the steps though, but don't think it was applicable since one step says " Install the software as you would normally do in Windows", which just isn't possible becuase for one, it's NOT windows, and clicking on the exe file returns an error. Also, I think that just by running winecfg, the "emulated" windows directory is created, so having to do this : > Locate the program you have just downloaded

Lets assume it is just in your home directory

5. To install Winzip type:
$ wine winzip90.exe   Isn't necessary I guess. 

Anyway, it sounds like reacocard was getting me on the right track, I believe. Just need clarification on the directory path etc. 

Doug

---

### Post by toasted on 2006-09-02
If you just double click the .exe what happens? When I had wine installed it would automatically run when you clicked an .exe file

---

### Post by Sweet Spot on 2006-09-02
You guys rock ! Thanks so much Toasted, that totally did the trick ! that was easier than I thought it would be, once the right steps were laid out. Thanks agian ! Hopefully I won't have any problems using it, but I've seen a bunch of people w/problems, so I might be back. :biggrin:

Doug

---

### Post by toasted on 2006-09-02
here's a tip
drag the file into the terminal and drop it... it will tell you the path

---

### Post by Sweet Spot on 2006-09-02
> **toasted said:**
> If you just double click the .exe what happens? When I had wine installed it would automatically run when you clicked an .exe file

Are you using KDE or Gnome ? Not sure if that's an issue. To answer your question, when I clicked on the .exe, I got an error message saying 
"can not view dvdshrinksetup32.exe". That's pretty much it. But dragging the exe into the terminal, and putting quotes around "wine/filepath/" as such, worked in an instant. It was pretty exciting actually. Not sure of why that worked for you as you've said. I guess mileage varies ?

Doug

P.S. Love your avatar.
P.P.S. Hey ! You JUST changed your avatar ! Like the other one better, but this one is pretty funny.

---

### Post by toasted on 2006-09-02
Dunno, I havent had wine for a while but it did do that as I recall and it always did it.. well the 6 or 8 times I tried it anyway. Wine was short lived with me 

I'm using Gnome

---

### Post by toasted on 2006-09-02
> **Sweet Spot said:**
> Are you using KDE or Gnome ? Not sure if that's an issue. To answer your question, when I clicked on the .exe, I got an error message saying 
"can not view dvdshrinksetup32.exe". That's pretty much it. But dragging the exe into the terminal, and putting quotes around "wine/filepath/" as such, worked in an instant. It was pretty exciting actually. Not sure of why that worked for you as you've said. I guess mileage varies ?

Doug

P.S. Love your avatar.
P.P.S. Hey ! You JUST changed your avatar ! Like the other one better, but this one is pretty funny.

LOL  Can't let the toast get moldy!

---

### Post by Sweet Spot on 2006-09-02
Unless your a bit sick of course, because then, mold can be pretty good for you... Just sayin'....

Doug

---

