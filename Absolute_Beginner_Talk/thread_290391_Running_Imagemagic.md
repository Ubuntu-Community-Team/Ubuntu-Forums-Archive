---
title: "Running Imagemagic"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2006-11-01
I have just installed imagemagic through Synaptic. How do I run it?

This is actually a generic question - how does one run programs that one has installed?

Thanks - Bill

---

### Post by xyz on 2006-11-01
Doesn't i show in Application > Graphics  or Alt + F2?

---

### Post by cairnsww on 2006-11-01
No - does that mean that I have a bad install? I have also tried to install gnuchess and it does not appear under games either. There did not seem to be anything wrong with the installation.

---

### Post by xyz on 2006-11-01
Strange! How about typing the prog's name in a terminal + Enter?
What happens then?

---

### Post by cairnsww on 2006-11-01
When I type "imagemagic" in the terminal, it says command not found. Of course the program may not be called "imagemagic"!

When I type "gnuchess" it executes gnuchess in terminal mode - ie it asks me for a move. I also installed eboard - I presume that somewhere the two have to be linked up.

But, going back to my generic question. How is this meant to work. How am I meant to run an arbitrary program without going to the Allplications menu? In Windows terms, where do I find the equivalent of an exe file and run it?

Bill

---

### Post by xyz on 2006-11-01
I openend Synaptic and typed a "Search" for 'imagemagic' and it found 'imagemagick'. So it is imagemagick that was installed and that must be the command line in a terminal.

Sometimes I go into Application; other times Alt + F2 and of course typing the correct name into a terminal. As far as I know that's how most of us openend stuff.

There's no .exe in Ubuntu.

---

### Post by cairnsww on 2006-11-01
No joy from typing "imagemagick" with a "k".

Yes, I know there are no exe files in Linux. That is why I said "the equivalent of". What I mean is this - under Windows I can go to Program Files and find the exe file for, say, Word. I click on it and it runs.

I know that Linux does things differently. I know that some stuff goes under usr and some under other directories. But, to a beginner like me, this is confusing - if the application that I want to run does not come up under the applications menu, I have no idea where to find it and how to run it.

---

### Post by xyz on 2006-11-01
Well,well,well...what have we here?
For the sake of helping, I reopened Synaptic and "Mark imagemagick for Installation" + Apply > OK.
Then I hit ALT + F2 and scrolled down to 'imagemagick' and clicked on it.
And it is there. I don't really know why it doesn't work for you.

Maybe try uninstalling it and reinstalling it either through Synaptic or in a terminal:
```
sudo aptitude install imagemagick
```
Hope it works for you.

---

### Post by xyz on 2006-11-01
imagemagick is in /usr/share/ImageMagick-6.2.4
To take a look at it, go to Places > Computer...open File System and click on "usr" then on "share" and scroll down to Imagemagick.

I also found this link which may help you out: (check what **magick**) has to say:
[MAGICK]("http://redux.imagemagick.org/discussion-server/viewtopic.php?p=23087&sid=739794f8e4b5b47cdc7228136f51ab6e")
Also this:
[Examples of ImageMagick Usage ]("http://www.cit.gu.edu.au/~anthony/graphics/imagick6/")
Finally:
[Imagemagick]("http://www.imagemagick.org/script/index.php")

---

### Post by jaboua on 2006-11-01
Lots of the imagemagick utils are just CUI apps, run the command "display" to launch a GUI

---

### Post by xyz on 2006-11-01
> **jaboua said:**
> Lots of the imagemagick utils are just CUI apps, run the command "display" to launch a GUI
That's it 'display'...thanks jaboua!
Would you mind taking a minute to explain why you can't run it by typing 'imagemagick' in a console?

---

### Post by 3rdalbum on 2006-11-01
Imagemagick is simply the name given to a collection of programs. Imagemagick is not the name of a program itself.

Here's a tip: Go to the terminal and type:

```
man imagemagick
```

Then it gives you a name and description of all the programs that comprise Imagemagick.

---

### Post by cairnsww on 2006-11-01
Thanks for your help - I still do not get imagemagick on the applications display - nor after alt-F2. I did re-install and it did not seem to make any difference.

"Display" does bring up imagemagick to display a file. Thanks.

Perhaps I need to understand more about imagemagick before asking more questions! But, again, your help is much appreciated.

---

