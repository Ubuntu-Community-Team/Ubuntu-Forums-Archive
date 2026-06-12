---
title: "[SOLVED] help with this bash script to move files.."
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-01-29
hi,

i have a crontab set up to run this

```
#!/bin/sh

exec mv /media/hdd_4/Incoming/* /media/hdd_4//sort/
```

dosent work...

any ideas?

thanks

---

### Post by Arthur Archnix on 2008-01-29
I'm no pro at scripts or bash, but this looks odd to my unskilled eyes:
> exec mv /media/hdd_4/Incoming/* /media/hdd_4**//**sort/

Maybe get rid of that second /   ?   Eg. instead of hdd_4//sort/ write hdd_4/sort

Sorry man... just guessing.

---

### Post by emarkd on 2008-01-29
It may not make a difference, but you don't really need that exec in there.  And I agree with Arthur; lose the double slash.

```
#!/bin/sh

mv /media/hdd_4/Incoming/* /media/hdd_4/sort/
```

should work just fine.

---

### Post by hopelessone on 2008-01-29
for some reason it dosen't work...

(the // was typing error in hte post not in the script...sorry...)

---

### Post by emarkd on 2008-01-29
Do you get an error message?  Have you checked permissions in those directories?  Are you running this using your account's crontab or root's?  Did you make your script executable?  Did you run your script from the terminal just to test it?

---

### Post by hopelessone on 2008-01-29
in the terminal:

[email]firebox@firebox-desktop:~/.aMul[/email]e$ chmod +x .amule_finish
[email]firebox@firebox-desktop:~/.aMul[/email]e$ .amule_finish
bash: .amule_finish: command not found
[email]firebox@firebox-desktop:~/.aMul[/email]e$

---

### Post by emarkd on 2008-01-29
In Linux, you always have to specify the path.  It's a security measure.  You can specify the current path by doing:

```
./.amule_finish
```

---

### Post by hopelessone on 2008-01-29
ok ..thanks..

whoops...forgot a line here:

mv /media/hdd_4/.this bin/Incoming/* /media/hdd_4/this bin/sort/

[email]firebox@firebox-desktop:~/.aMul[/email]e$ ./.amule_finish
mv: target `bin/sort/' is not a directory: No such file or directory
[email]firebox@firebox-desktop:~/.aMul[/email]e$ 

i think the problem is the space in "this bin"

---

### Post by emarkd on 2008-01-29
you got it.  the easiest thing to do is to replace that with an '_' or something, but you may be able to wrap that in quotes to get it to work if you really want your spaces.  Like this:

```
mv "/media/hdd_4/this bin/Incoming/*" "/media/hdd_4/this bin sort/"
```

---

### Post by hopelessone on 2008-01-29
[email]firebox@firebox-desktop:~/.aMul[/email]e$ ./.amule_finish
mv: cannot stat `/media/hdd_4/.this bin/Incoming/*': No such file or directory
[email]firebox@firebox-desktop:~/.aMul[/email]e$

---

### Post by emarkd on 2008-01-29
Ok, try just wrapping the path in quotes.  I'm not sure because I never use spaces because of these sorts of problems.  Try:

```
mv "/media/hdd_4/.this bin/Incoming"/* "/media/hdd_4/.this bin/sort/"
```

---

### Post by Joeb454 on 2008-01-29
Also if there's a space I'm sure you can use the escape sequence, e.g.

```
cd /home/me/this\ has\ spaces/
```

Note how I used "\ " (without quotes :p) to get the space in there

---

### Post by hopelessone on 2008-01-29
Joeb454 that fixed it...

taa..

---

