---
title: "Where is my tremulous directory"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by marlocarloandro on 2008-04-20
C:programs??? 
I'm new to Ubuntu so I haven't figured out how directories work.
I need to find the directory that a game called tremulous is in. anyone know how?

---

### Post by Whiffle on 2008-04-20
Its likely that its spread out among several directories, which part of it are you looking for?  If its settings, its in a directory that starts with a . in your /home/username directory, something like /home/username/.tremulous

---

### Post by marlocarloandro on 2008-04-20
Well the thing is. I want to run a dedicated server.
I followed the instructions at tjw.org/tremulous/SETUP.txt
but I could not get passed

```
3) replace the tremded.x86 file with the one from this site (and make it
   executable)
   
  'wget http://tjw.org/tremulous/linux/tremded.x86'
  'chmod a+x tremded.x86'
  'cp tremded.x86 /where/tremulous/is/installed/'
```
because I dont know where its installed:(

---

### Post by Dr Small on 2008-04-20
Try:
```
whereis tremulous
```

---

### Post by marlocarloandro on 2008-04-20
```
~$ whereis tremulous
tremulous: /usr/lib/tremulous /usr/games/tremulous /usr/share/man/man6/tremulous.6.gz

```
those were the outputs. Which one should in install the tremded in?

---

### Post by Whiffle on 2008-04-20
i should thing /usr/games/tremulous, although i think thats a directory.  I'd poke around inside it and see whats there.

---

### Post by nofrendo on 2008-04-20
You probably don't have tremded installed because it doesn't have the option to install it when you do it through Synaptic. You have to go to the tremulous website and download it from there. But uninstall it through APT or Synaptic first. Then I believe it's in /usr/lib/tremulous

---

### Post by marlocarloandro on 2008-04-20
just tried that and I tried it at home/myname/.trem

all i got wa ```

----------------------
812 files in pk3 files
Sys_Error: Couldn't load default.cfg

```

---

### Post by marlocarloandro on 2008-04-20
nofrendo I think you are talking the Backport.
I installed the backport when I got trem.
and I think Server.cfg might have to be in the trem directory.

---

### Post by gsiliceo on 2008-06-16
The ubuntu repositories install tremulous and uses a script to call it and tell it where is the base data, the script is this 
/usr/games/tremulous
And you can see that binary for the server is here
/usr/lib/tremulous-server
And thats the folder you are tring to find.

You installed the tremulous-server packaged did you?

Once you are done to execute the server you'll need to call another ubuntu specific script, just type tremulous-server and you'll have your running server.

If you manage to get a working custom qvm please post as i can't.
EDIT:
GOT IT WORKING, at least NEROS QVM [http://tremulous.net/forum/index.php?topic=7484.0](http://tremulous.net/forum/index.php?topic=7484.0)

---

