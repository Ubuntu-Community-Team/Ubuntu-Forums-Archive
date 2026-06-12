---
title: "Installing fonts?"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-05-13
I checked the help section and it states:

"Copy the font file to the $HOME/.fonts directory of the user. If you drag the font file to the fonts:/// location in the file manager, the font file is copied to the $HOME/.fonts directory."

I cannot find this directory. I'm running Breezy Badger.:)

A search for "Font" turns up lots of choices.  I have a font I'd like to install, just don't know where or how.

---

### Post by bluevoodoo1 on 2006-05-13
the .fonts directory is a hidden directory in your home folder.

to show hidden files from Nautilus...
ctrl+h
or 
View > show hidden files

---

### Post by georgetoon on 2006-05-13
[QUOTE=bluevoodoo1]the .fonts directory is a hidden directory in your home folder.

to show hidden files from Nautilus...
ctrl+h
or 
View > show hidden files[/QUOTE]

My apologies...I forgot to mention that I did do that. I can see all files including hidden files. 

.font is not there.

---

### Post by bluevoodoo1 on 2006-05-13
Oh! Well you can make a folder then!

```
mkdir .fonts
```

or with nautilus, right-click create folder, name it .fonts

you should be all set.

---

### Post by georgetoon on 2006-05-13
[QUOTE=bluevoodoo1]Oh! Well you can make a folder then!

```
mkdir .fonts
```

or with nautilus, right-click create folder, name it .fonts

you should be all set.[/QUOTE]

Whaaa????!!!:):) That's all there is to it??

Okay, so I created the folder **.fonts**, and then dropped in the font i needed. I then opened up OpenOffice Writer, went to the drop down list of fonts, and there it is!

Wow! that is slick!:)

so, whee are all the other fonts stored? Or don't I want to know for fer of messing things up?

One more question...so if I want to add more fonts, all I need do is drag 'em into the .fonts folder?

---

### Post by bluevoodoo1 on 2006-05-13
The fonts you have in your .fonts folder are only available to you. /usr/share/fonts has a bunch of fonts available to all users.  (if you don't have other user accounts then this doesn't matter).

Yup, just put them in .fonts !

---

### Post by georgetoon on 2006-05-13
Thank you so much for all your help.:)

---

### Post by bluevoodoo1 on 2006-05-13
:):)

---

