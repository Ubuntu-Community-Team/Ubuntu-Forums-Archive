---
title: "Help locked out of /Home"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-02-21
I dunno what i did last night but somehow i allowed all read/write access to my home dir. Whenever i start up, i get this message

```
Users $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $Home directory must be owned by user and not writable by other users.
```

Though i was still able to log in to try and fix the problem. First of all i tried right clicking and changing the permissions through there but they wouldn't save. Then i tried in the terminal setting the permissions to 644 as it said. 

When i logged out i got a message saying my session only lasted 10 seconds and viewed the log and it couldn't create anything in my /home directory. Permission denied. 

I'm not too sure, nor can i find the correct chmod command to run from bash...Can anyone help please?

---

### Post by Muppeteer on 2007-02-21
Bump :(

---

### Post by Bachstelze on 2007-02-21
(Replace foobar with your username)

```

sudo chown foobar:foobar /home/foobar
sudo chmod -R 644 /home/foobar
```

---

### Post by AtrejuT on 2007-02-21
I'm not really an expert but you might try this:
- go to a terminal (Ctrl+Alt+F1) and log in there.
- type 
```

sudo chown -R yourusername:yourusername /home/yourusername 

```

where obviously you replace yourusername by your username ;-)
next you could do something like 

```

sudo chmod -R 644 /home/yourusername

```


oups, too late...


I hope I got the syntax right - good luck

atreju

---

### Post by Muppeteer on 2007-02-21
That didn't work :( 

I keep getting the following:
```
xauth: timeout in locking authority file //.serverauth.4186
timeout in locking authority file //.Xauthority
X: user not authorised to run the X server, aborting.giving up.
```

Don't like the sound of that...Any more suggestions? :(

---

### Post by AtrejuT on 2007-02-21
thats strange...

I can just guess - 

what are the actual permissions of these files?

```

ls -la .Xauthority
ls -la .serverauth*

```

---

### Post by Muppeteer on 2007-02-21
Ok the permissions of .Xauthority is -rw-r--r-- 1

And it said file not found for .serverauth...:confused:

---

### Post by taurus on 2007-02-21
What's the output of this command?

```
ls -la /home
```

---

### Post by Muppeteer on 2007-02-21
I tried again at the bash prompt but this time i set the permissions to 777. It's only when i set it to 644 i have problems...

I'm still getting the first error message and everyone has full read write access...but at least i'm able to log in.
```
Users $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $Home directory must be owned by user and not writable by other users.
```

Trying to understand tutorials on permissions, just not making sense :confused:

---

### Post by taurus on 2007-02-21
Boot into recovery mode and at the prompt, do

```
chmod -R 755 /home/**muppeteer**
chmod 644 /home/**muppeteer**/.dmrc
shutdown -r now
```
Assuming **muppeteer** is your login name.  Now, see if you can log in again.

---

### Post by Muppeteer on 2007-02-21
That worked a treat! 

Thanks a lot! :)

---

### Post by sirmrmatt on 2007-03-02
Wowsers!

Thanks, worked for me too.

Now just looking to fix this "failed to initialize HAL!" thingie...off to forum digging I go!

Thanks again!

- Matt

---

