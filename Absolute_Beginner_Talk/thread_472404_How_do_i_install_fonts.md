---
title: "How do i install fonts?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-13
I have a fonts folder in my USB, i want to copy it to the Ubuntu Fonts Folder

How do i do that?

I can't just copy and paste coz i don't have permission

I want to copy the fonts from a folder named "k" in /media/disk
to the fonts folder in ubuntu called "fonts:///"

---

### Post by Kobalt on 2007-06-13
You need to put your .tff files in the .fonts folder inside you Home : it's a hidden folder, pres Ctrl+H to see it/hide it.

---

### Post by mlentink on 2007-06-13
You might try to copy and paste with root permissions. 
Just precede the command with 'sudo', which means something like 'as superuser do...'

e.g.
```
sudo cp /thisdirectory/thisfile /thatdirectory/thatfile
```

---

### Post by jcronkhite on 2007-06-13
While in your home directory, you can show the hidden directories (such as ".icons, .fonts, etc") if you use "CRTL+H".  This might make it easier for you to understand what's going on there.

---

### Post by bamesah on 2007-06-13
Ok thx guys, i will try this command thing and reply

---

### Post by bamesah on 2007-06-13
I want to copy the fonts from a folder named "k" in /media/disk 
to the fonts folder in ubuntu called "fonts:///"

I wrote: 

```
sudo cp /media/disk/k /fonts:///
```

it says :

Target fonts:/// is not a directory, no such file or directory

---

### Post by dptxp on 2007-06-13
I have kde-core installed on uBUNTU.
There is Add Fonts in System Menu. I log with kde to do this job.

Unfortunately Gnome does not have it.

---

### Post by drowner on 2007-06-13
edit: kobalt has the answer

its a hidden folder, so browse to home, then press ctrl+h. and paste the files in ./fonts

---

### Post by dptxp on 2007-06-13
I had to resort to installing from kde as I wanted fonts from my Windows Fonts folder and I found it locked in Ubuntu. Just could not copy them. Could have copied to somewhere else first and added to .fonts in /home.

---

### Post by bamesah on 2007-06-13
> **drowner said:**
> edit: kobalt has the answer

its a hidden folder, so browse to home, then press ctrl+h. and paste the files in ./fonts

That worked Thank you

---

### Post by gn2 on 2007-06-13
To answer the original question, how to install fonts, that's easy, use Automatix.

Link in my sig.

---

### Post by bamesah on 2007-06-13
Thanks everbody , i installed the fonts

---

### Post by drowner on 2007-06-13
> **gn2 said:**
> To answer the original question, how to install fonts, that's easy, use Automatix.

Link in my sig.

My solution didn't involve installing another program, therefore, my solution is easier.


Safer, too

---

### Post by forrid on 2007-06-13
> You need to put your .tff files in the .fonts folder inside you Home : it's a hidden folder, pres Ctrl+H to see it/hide it.

thanks, but, my $HOME has not a hidden folder named ".fonts".

---

### Post by mlentink on 2007-06-13
> **forrid said:**
> thanks, but, my $HOME has not a hidden folder named ".fonts".

In that case you can easily create one
```
mkdir .fonts
```
Then copy your fonts into that as per the above instructions.

PLease be aware that fonts copied to the .fonts directory in your home folder are only visible/useable by that specific user. As you will usually be the only person to use your machine that is not much of a problem.
If you want your fonts to be available to all users of the system, they should go to /usr/share/fonts, if I remember correctly

---

### Post by gn2 on 2007-06-13
> **drowner said:**
> My solution didn't involve installing another program, therefore, my solution is easier.


Safer, too

Think that on close examination you'll find it was Kobalt's solution, and it's only easier if you've got the font files available, and know (and remember) what the terminal commands are.

Automatix just takes a few clicks of the mouse, and it's perfectly safe to use.

Still, whatever method suits, it's nice to have choices. :-)

---

### Post by drowner on 2007-06-13
i said it was kobalt's solution, no offence meant kobalt, and he DID have the fonts, and he ended up doing it with a few clocks of the mouse anyway.

---

