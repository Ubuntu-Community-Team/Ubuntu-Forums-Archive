---
title: "Fonts"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-29
Hi,

I've asked this question before but no one 'round at the time seemed to know. 
I have some fonts (ttf) which i would like to install.

In KDE this was a symple matter of going to control panel and clicking on the add font button. However, i see no such function here in Gnome. But surely there is a way.

I would dearly appreciate any help in this regard,

sophtpaw

---

### Post by maruchan on 2005-07-29
Open up the .fonts folder in your home dir and drag n' drop. Works for both KDE and Gnome.

---

### Post by sophtpaw on 2005-07-29
[QUOTE=maruchan]Open up the .fonts folder in your home dir and drag n' drop. Works for both KDE and Gnome.[/QUOTE]

O.k, are you saying that i already have a .fonts folder in my home dir? or do i create one to drag n'drop into?

Either way how do i either 1. open fonts folder in home dir or 2 create a folder called .fonts in home dir?

thank you


sophtpaw

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=sophtpaw]O.k, are you saying that i already have a .fonts folder in my home dir? or do i create one to drag n'drop into?

Either way how do i either 1. open fonts folder in home dir or 2 create a folder called .fonts in home dir?

thank you


sophtpaw[/QUOTE]

You have to tell nautilus to view hidden folders.

---

### Post by sophtpaw on 2005-07-29
[QUOTE=poofyhairguy]You have to tell nautilus to view hidden folders.[/QUOTE]

Naughtylus?

can you please say more? Remember you are talking to a complete Newbie/nincompup  ](*,) 

thx

sophtpaw

---

### Post by maruchan on 2005-07-29
Use the "places" menu (next to applications) to navigate to your home folder. If you are doing this, you are using Nautilus. It's just the file viewer.

Next go to the view menu and tell it to show hidden files.

After you do this, you should see a folder called ".fonts". Folders with a "." (period) in front of them are "hidden" folders.

Open up .fonts by double-clicking it, and move your font files into this folder. You have just installed new fonts.

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=sophtpaw]Naughtylus?

can you please say more? Remember you are talking to a complete Newbie/nincompup  ](*,) 

thx

sophtpaw[/QUOTE]


LoL. Sorry. Its hard to click off sometimes. Nautilus is the file program for windows. Its the program that starts when you look at your home folder. Where the file icons are. 

Any file with a "." before it is a hidden file. When you open you home folder, that files exists but nautilus can't see it. One of the options fromt eh menu at the top (I'm not on Ubuntu now so I can't tell you exactly) will say "view hidden files." Click it and you will see the fonts folder.

---

### Post by sophtpaw on 2005-07-29
[QUOTE=poofyhairguy]LoL. Sorry. Its hard to click off sometimes. Nautilus is the file program for windows. Its the program that starts when you look at your home folder. Where the file icons are. 

Any file with a "." before it is a hidden file. When you open you home folder, that files exists but nautilus can't see it. One of the options fromt eh menu at the top (I'm not on Ubuntu now so I can't tell you exactly) will say "view hidden files." Click it and you will see the fonts folder.[/QUOTE]


thx. However, there is no menu at the top nevermind anything about hidden files.
I have gone to Places and Home folder and put in the search box, .fonts / fonts /.font/font/hidden files etc, but i get nothing back. 

I don't know if i'm doing it properly or not or whether i just don't have a file, hidden or not, called font of any kind

???


any further suggestions please?


sophtpaw

---

### Post by sophtpaw on 2005-07-29
[QUOTE=sophtpaw]thx. However, there is no menu at the top nevermind anything about hidden files.
I have gone to Places and Home folder and put in the search box, .fonts / fonts /.font/font/hidden files etc, but i get nothing back. 

I don't know if i'm doing it properly or not or whether i just don't have a file, hidden or not, called font of any kind

???


any further suggestions please?


sophtpaw[/QUOTE]



After search in Home proved futile, as mentioned above, i started doing searches through the filesystem. When i did search in 'usr' i got 1 file back :
README.fonts.gz  this is file type gzip 

but it is not what you were talking about?

Thank you for helping a blind man across the street

sophtpaw

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=sophtpaw]


any further suggestions please?


sophtpaw[/QUOTE]

sure. Put tis command in the terminal:

> gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true

and look for the menus at the top.

---

### Post by sophtpaw on 2005-07-29
[QUOTE=poofyhairguy]sure. Put tis command in the terminal:



and look for the menus at the top.[/QUOTE]


Big Thx Poofyhairguy!

You have just helped define who you are in a large way!
 what a command line! That has made a big difference to how i view my HOME folder now! mind you i still cant seem to find the font folder. 

I went to terminal emulator and did mkdir ~/.fonts (or something to that effect)
It now says that there is a file '.fonts in /home/conrad but i do not see it. And why not just /home why /home/conrad

i shall persist

sophtpaw

---

### Post by sophtpaw on 2005-07-29
[QUOTE=sophtpaw]Big Thx Poofyhairguy!

You have just helped define who you are in a large way!
 what a command line! That has made a big difference to how i view my HOME folder now! mind you i still cant seem to find the font folder. 

I went to terminal emulator and did mkdir ~/.fonts (or something to that effect)
It now says that there is a file '.fonts in /home/conrad but i do not see it. And why not just /home why /home/conrad

i shall persist

sophtpaw[/QUOTE]


We have Lift off!

I have my fonts complete \\:D/ 
the folder .fonts i created with mkdir /.fonts is there, but under /home/conrad
So when i was searching under Home folder it wouldn't find it. Hence i was pulling my hair out. The computer was telling me in command line that it was there but the search wouldn't show it to me. and when i looked under the filetree it wasn't there either.
The breakthrough was that long commandline which enabled me to have a different look into my Home folder. 
For some reason it is organised / then /home which makes sense so far but then /home/conrad which is where all my directories (?) are. Which is fine but then why when i do a search under Home it doesn't also have search under /home/conrad?

anyhow copied and pasted my ttf's into /home/conrad/fonts like it was suggested to me at the beginning and i have lift off. Its nife to have a happy ending

Thank you

sophtpaw

---

