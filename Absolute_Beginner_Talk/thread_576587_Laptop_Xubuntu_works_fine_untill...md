---
title: "Laptop Xubuntu works fine untill.."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-15
well basically until its first FSCK boot scan.
its doing now but when it gets to 68.1%

then i get the error

```
 Buffer I/O error on device hda3, Logical block 1173103468 1%

then it carries on with numbers following in suit.
short while after:

FSCK died with Exit status 4
/dev/hda3 UNEXPECTED CONSISTENCY 
```

why has it suddenyl stopped working?
theres more

```

bash: apt-get: command not found
bash: dircolours: command not found
bash: sudo: command not found 
```

it was a breeze until  now.

ive had Ubuntu on my desktop for 6months and about a month on this laptop.
i was using it to browse through then restarted.

so what the.... has gone on!? no sudo? no apt? weird..

---

### Post by benuski on 2007-10-15
It looks like your hard drive is dying.  I got the same error messages, ran my hard drive diagnostic, and it came up with an error too.  I took it to my school's IT, and they replaced my hard drive.  So I would reccomend using your hard drive's diagnostic utility, and hope that something else went wrong.

---

### Post by LowSky on 2007-10-15
It's most likely a bad hard drive. You got to remember that your laptop has moving parts inside it and cant be flung around like a soccer ball.

---

### Post by Orbital75 on 2007-10-15
I'm thinking you may have some bad Sectors on your drive..... 
Give Spinrite a try, it worked for me on an old Windows 2000 installation.
SpinRite is OS independent so it will run on anything, it just looks at your
drive not your OS.  

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

---

### Post by skymera on 2007-10-15
thanks :D
i done a reinstall anyway.

but i get a really strange boot :lol:

if i boot straight from HD it says invalid boot sector.

however! if i ut the live CD in..let it boot from CD till the main menu:

```
 
install
install in safe graphics
blah
blah
boot to first disk 
```

if i boot to first disk..my GRUB loads!?

it works when i use the live cd? but when i dont..wont boot.

---

### Post by skymera on 2007-10-17
ok i got spinrite, its been going for 3 hours, 90% it bleeped  and it said its 'initializing dynastat recovery system'

and it dosent seem to do anythin now..
the HD light is on so im going to leave it.

is this normal?

---

