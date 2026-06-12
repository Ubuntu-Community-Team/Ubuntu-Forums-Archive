---
title: "tar isn't working"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by blastthisinferno on 2007-07-08
I'm having trouble with tar.  I'm trying to extract a tar file for gdm.  I'm first trying to see what's in the tar file by ```
tar t ~/55513-Leaf_u.tar.gz
```After I press enter it doesn't do anything.  Nothing, it just stalls or something.  I have to press ctrl+C to get back to where I can input a command.

The other thing that is happening when I'm trying to extract the file is this```
tar xzvf ~/55513-Leaf_u.tar.gz
Leaf/GdmGreeterTheme.desktop
tar: Leaf/GdmGreeterTheme.desktop: Cannot open: No such file or directory
tar: Skipping to next header
Leaf/configuration.xml
tar: Leaf/configuration.xml: Cannot open: No such file or directory
tar: Skipping to next header
Leaf/bg.jpg
tar: Leaf/bg.jpg: Cannot open: No such file or directory
tar: Skipping to next header
Leaf/screenshot.jpg
tar: Leaf/screenshot.jpg: Cannot open: No such file or directory
tar: Skipping to next header
tar: Error exit delayed from previous errors
```

---

### Post by Nekiruhs on 2007-07-08
```
man tar
```
Says that the command is tar -xvvf /PATH/TO/TARFILE

---

### Post by phidia on 2007-07-08
Is there a typo in the command you listed?

You want > tar -t note the hypen mark.
And the xzvf argument is ok but it needs to be prefaced by a "-"

---

### Post by blastthisinferno on 2007-07-08
the hypen has the same result.  I still have to press ctrl+C to type anything else.

---

### Post by AlexenderReez on 2007-07-08
i wonder are you sure you tar.gz file not corrupt ...?how about just extract by using mouse right button.....

---

### Post by AlexenderReez on 2007-07-08
> **blastthisinferno said:**
> I'm having trouble with tar.  I'm trying to extract a tar file for gdm.  I'm first trying to see what's in the tar file by ```
tar t ~/55513-Leaf_u.tar.gz
```After I press enter it doesn't do anything.  Nothing, it just stalls or something.  I have to press ctrl+C to get back to where I can input a command.

[/CODE]

if just want to install gdm theme..just move that tar file to gdm setup...don't need to extract it.....

---

### Post by blastthisinferno on 2007-07-08
> **reez0105 said:**
> i wonder are you sure you tar.gz file not corrupt ...?how about just extract by using mouse right button.....How do you right click on the file in fluxbox?  I'm not seeing a file.  I'm new to fluxbox.

---

### Post by blastthisinferno on 2007-07-08
> **reez0105 said:**
> if just want to install gdm theme..just move that tar file to gdm setup...don't need to extract it.....Is gdm setup a directory?

---

### Post by RedSquirrel on 2007-07-08
That's a nice-looking gdm theme.

[http://www.gnome-look.org/content/show.php/Leaf?content=55513](http://www.gnome-look.org/content/show.php/Leaf?content=55513)

Here's what you have to do:

Go into your Fluxbox menu:

Apps -> System -> GDM setup

Click the 'Local' tab.

Click the 'Add' button

Browse to the tar.gz file you downloaded.

Click 'Install'.

That's all you have to do. No need to extract anything.

That should work fine (it did for me) assuming there is nothing wrong with your downloaded file.

Here is a sample of tar commands:

tar tf filename
tar tvf filename

tar xvzf filename
tar xvjf filename

tar xzf filename
tar xjf filename

tar czf filename
 tar cjf filename
 

etc.

And you don't need the "-" in front of your options, but you can put it there if you want to. ;)

---

### Post by blastthisinferno on 2007-07-08
RedSquirrel you are the bomb....or rather human, but you get the point.  That worked.  I just assumed that there was a tar file and it should be unzipped.  Thanks again everyone for your comments.

---

