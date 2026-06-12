---
title: "Using a new splashscreen"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by sc2 on 2007-11-15
I was following the instruction given here: [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

I'm having trouble with this portion of installation:

```
 
cd
cd Desktop
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so

```

Help?


Specifically, I get this error:

```

will@will-desktop:~$ cd
will@will-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory

```

And I won't go any further in case of breaking something.. :)

---

### Post by Paul820 on 2007-11-15
Type
> cd ~/Desktop

---

### Post by sc2 on 2007-11-15
> **Paul820 said:**
> Type



```

will@will-desktop:~$ cd
will@will-desktop:~$ cd ~/Desktop
will@will-desktop:~/Desktop$ sudo cp usplash-theme-fingerprint.so/usr/lib/usplash
[sudo] password for will:
cp: missing destination file operand after `usplash-theme-fingerprint.so/usr/lib/usplash'
Try `cp --help' for more information.
will@will-desktop:~/Desktop$ 

```


:confused:

I have usplash-theme-fingerprint.so in my Desktop folder.

---

### Post by Paul820 on 2007-11-15
You need a space between the filename and the destination directory
> will@will-desktop:~/Desktop$ sudo cp usplash-theme-fingerprint.so /usr/lib/usplash

---

### Post by sc2 on 2007-11-15
> **Paul820 said:**
> You need a space between the filename and the destination directory


While I'm tinkering with this, did you make your forum avatar with Blender? ;)

---

### Post by Paul820 on 2007-11-15
Yes, sure did. :) It was from a tutorial though, i am still learning to use it as it's my first time doing 3D. There is lots to learn. :)

---

### Post by sc2 on 2007-11-15
```

will@will-desktop:~$ sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
cp: cannot stat `usplash-theme-fingerprint.so': No such file or directory

```


Now I wanted to point out this was odd, this file is in the desktop folder, I quadruple checked. Am I missing something? -_-

I uploaded a photo so that you can see the file location..it is definitely in the desktop. [http://img36.picoodle.com/img/img36/5/11/15/f_weirddesktom_7cd34d1.png](http://img36.picoodle.com/img/img36/5/11/15/f_weirddesktom_7cd34d1.png)

---

### Post by Paul820 on 2007-11-15
No, that looks fine. I will go through the tutorial and see what is going on.

EDIT: I have just done the same command as you are trying to do and it copied straight over. No problems at all.

---

### Post by Paul820 on 2007-11-15
Do this if it's being annoying.
From the terminal type or copy and paste
> gksudo nautilus
Now when the new window opens, browse to /usr/lib/usplash and drag that file from the desktop into that folder. Then shut the window. You will get it in there. :)

---

### Post by sc2 on 2007-11-15
> **Paul820 said:**
> Do this if it's being annoying.
From the terminal type or copy and paste

Now when the new window opens, browse to /usr/lib/usplash and drag that file from the desktop into that folder. Then shut the window. You will get it in there. :)



Alright, I was confused by what you wanted my to do, so I tried to do it on my own based off of what I thought your instructions were saying...AND IT WORKED!! Now I just have to restart and stuff..

Thank you!

---

### Post by Paul820 on 2007-11-15
No problem. Glad to hear you got it going. :)

---

### Post by sc2 on 2007-11-15
> **Paul820 said:**
> No problem. Glad to hear you got it going. :)

Just kidding. :( I restarted my computer, and the splash screen is black. It isn't working, but it didn't say in terminal I had any errors! :(


:confused::confused::confused::confused::confused:

---

### Post by Paul820 on 2007-11-15
Did you do the last two lines of the instructions?

EDIT:
These ones
>  sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so
And this
> sudo update-initramfs -u

---

### Post by jordank on 2007-11-15
remember to capitalize

---

### Post by Paul820 on 2007-11-15
> **jordank said:**
> remember to capitalize
Capitalize what? :confused:

---

### Post by sc2 on 2007-11-15
> **Paul820 said:**
> Did you do the last two lines of the instructions?

EDIT:
These ones

And this



Yes.


edit: Here is what I mean by no errors at all: [http://img29.picoodle.com/img/img29/5/11/15/f_selected2m_42b29c5.png](http://img29.picoodle.com/img/img29/5/11/15/f_selected2m_42b29c5.png)

Shouldn't it be working? -_-

---

### Post by Paul820 on 2007-11-15
I get the same thing. A flashing cursor in the top left corner and it's all black. Maybe it's broken???

---

### Post by sc2 on 2007-11-15
> **Paul820 said:**
> I get the same thing. A flashing cursor in the top left corner and it's all black. Maybe it's broken???

I would hope not..it looks pretty sweet.

[http://gnome-look.org/content/preview.php?preview=2&id=50468&file1=50468-1.jpg&file2=50468-2.jpg&file3=50468-3.jpg&name=Usplash+Theme+-+Fingerprint](http://gnome-look.org/content/preview.php?preview=2&id=50468&file1=50468-1.jpg&file2=50468-2.jpg&file3=50468-3.jpg&name=Usplash+Theme+-+Fingerprint)

Check that out...damn..

---

### Post by Paul820 on 2007-11-15
There seems to be a lot on gnome-look having problems with it.

---

