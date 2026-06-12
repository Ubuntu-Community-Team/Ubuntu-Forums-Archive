---
title: "Ok now Dapper has just gone a little weird on, please help!!!"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-08-07
ok it all started aboiut 5 minutes ago when i decided i wanted to fiddle with my machine and now i get this error message for almost everything i try to do in the terminal

mike@Dapper Drake:~$sudo apt-get install samba
sudo: unable to lookup Dapper Drake via gethostbyname()

HEEEEEEEEEEEELP

peace

DK

---

### Post by davebgimp on 2006-08-07
> **DiscoKiller said:**
> ok it all started aboiut 5 minutes ago when i decided i wanted to fiddle with my machine and now i get this error message for almost everything i try to do in the terminal

mike@Dapper Drake:~$sudo apt-get install samba
sudo: unable to lookup Dapper Drake via gethostbyname()

HEEEEEEEEEEEELP

peace

DK

What exactly were you "fiddling" with on your machine?

---

### Post by cantormath on 2006-08-07
> **DiscoKiller said:**
> ok it all started aboiut 5 minutes ago when i decided i wanted to fiddle with my machine and now i get this error message for almost everything i try to do in the terminal

mike@Dapper Drake:~$sudo apt-get install samba
sudo: unable to lookup Dapper Drake via gethostbyname()

HEEEEEEEEEEEELP

peace

DK

You changed your hostname didnt you?

---

### Post by DiscoKiller on 2006-08-07
wouldnt you like to know??

hehe

no i was just trying to change my hostname to something a little nicer....but now it wont let me do anything.

my main aim tonight was to see whether or not i could get windows to see my shared folders on a LAN, but i`m not really bothere about that now, i just wanna be able to do .....anything with my machine...

peace DK

---

### Post by davebgimp on 2006-08-07
> **DiscoKiller said:**
> wouldnt you like to know??

hehe

no i was just trying to change my hostname to something a little nicer....but now it wont let me do anything.

my main aim tonight was to see whether or not i could get windows to see my shared folders on a LAN, but i`m not really bothere about that now, i just wanna be able to do .....anything with my machine...

peace DK

Have you tried step by step, reversing your "fiddlings"?

---

### Post by DiscoKiller on 2006-08-07
well.....yeah....:oops:

---

### Post by DiscoKiller on 2006-08-07
i`ve no idea what my hostname was...something weird like unknown987264987123698`74blah

---

### Post by cantormath on 2006-08-07
I just wrote a post about this,
[http://ubuntuforums.org/showthread.php?t=228493](http://ubuntuforums.org/showthread.php?t=228493)

---

### Post by powder on 2006-08-07
Have a look through this thread, perhaps you will find your solution. ;)

[http://ubuntuforums.org/showthread.php?t=78324](http://ubuntuforums.org/showthread.php?t=78324)

---

### Post by cantormath on 2006-08-07
> **powder said:**
> Have a look through this thread, perhaps you will find your solution. ;)

[http://ubuntuforums.org/showthread.php?t=78324](http://ubuntuforums.org/showthread.php?t=78324)

I think the problem is that he changed the hostname incorrectly or to something that is not valid...

this is what I would do, turn the machine on, if you are logined in or at the login prompt, 

press
```
<ctrl>+<alt>+F1
```
or F2 etc.

login 

```
sudo nano /etc/hostname,
```

nano is a text editor, if you dont have it, get it or use vi.

delete whatever is there, if anything, and type your hostname
ie
```
cantormath-laptop
```

then press
```
<ctrl>+x
```
to exit, type y to save and hit enter, cause you dont want to change the name of what file it saves to. hostname should already be typed in there.

added: if you are changing the hostname to something new, after you change  and save /etc/hostname, open /etc/hosts:

```
sudo gedit /etc/hosts
```
```

127.0.0.1 localhost 
127.0.1.1 <OLDHOSTNAME>
```

change the old hostname to the new hostname next to 127.0.1.1, save and reboot.

it should fix the problem...

if you have to use vi
```
<ctrl>+<alt>+F1
```
```
sudo vi /etc/hostname
```
hit the letter i, delete whatever is there, and type the hostname you want to use.
then type <esc>
then type <:> (and im mean <SHIFT>+<;>)
type wq (which means write and quit)
and reboot

added: again if hostname is new, change /etc/hosts file to have new hostname next to 127.0.1.1
```
sudo reboot 
```

lol, I just did that to myself..

---

### Post by DiscoKiller on 2006-08-07
unfortunately whatever i tr to do i keep getting that error message thingy...thinking i might just save myself the hassle and go for a complete reload...again

Thanks for your help guys, but TinyXP Beast Edition is gonna have to be my home for now!

Peace 

DK

---

### Post by cantormath on 2006-08-07
> **DiscoKiller said:**
> unfortunately whatever i tr to do i keep getting that error message thingy...thinking i might just save myself the hassle and go for a complete reload...again

Thanks for your help guys, but TinyXP Beast Edition is gonna have to be my home for now!

Peace 

DK

did you check your /etc/hosts and /etc/hostname file?
just change the hostname back to the old hostname.

again type the old hostname in /etc/hostname, and make sure in /etc/hosts that the new hostname is next to 127.0.1.1
ie
```
127.0.1.1 cantormath-laptop
```

are you using ubuntu or kubuntu?

---

### Post by DiscoKiller on 2006-08-12
After much deliberation i`ve decided that you guys, davebgimp cantormath and  powder, are legends. rememeber that. cheers guys i`ve sorted it now. many thanks to each of you.

peace

DK

---

