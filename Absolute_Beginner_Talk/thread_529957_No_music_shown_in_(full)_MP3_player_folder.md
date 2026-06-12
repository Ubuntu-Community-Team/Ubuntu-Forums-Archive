---
title: "No music shown in (full) MP3 player folder"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by mak123 on 2007-08-19
I have a Sandisk Sansa 1.0GB mp3 player, and I'm running Xubuntu Feisty.

Now, the music that's on my Sansa was synched when I was on Windows.

When I hook up my Sansa via USB (in either MSC or Auto Detect mode), a "1GB Removable Media" icon shows up on my desktop.

But, only my documents show up, and not my music files (which are there for sure because my Sansa is near capacity).

I remember having this issue while on Windows, but I was able to figure it out by choosing either MSC or Auto Detect.

Can anyone help?  Thanks!

---

### Post by Acglaphotis on 2007-08-21
Try cd'ing to the directory and then do 'ls' and post that here.

---

### Post by mak123 on 2007-08-21
> **Acglaphotis said:**
> Try cd'ing to the directory and then do 'ls' and post that here.

I'm sorry.  I'm not sure what you mean by "cd'ing" and "ls".  I'm eager to learn though!  Thanks for your response.  I appreciate your help.

---

### Post by Acglaphotis on 2007-08-21
i ment opening a terminal (applications>accesories>Terminal and doing these commands)

```

cd /media/Sansagoeshere/

```

when you are there do a 

```

ls

```

That should list all of the files in the directory. If that doesnt work type

```


gksudo nautilus /media/Sansagoeshere


```

Then pressing Control+H. If that doesnt work try it on another computer and see f the problem persist.

Sorry about not being clear enough in my first post : ).

EDIT:Im going to sleep. I'll be back in 12 hours.

---

### Post by mak123 on 2007-08-21
After cd'ing and ls, I get the following files:
> AUDIBLE  MTABLE.SYS  RES_INFO.SYS  SYS_CONF.SYS          version.sdk
Docs     RECORD      Secondaries   TempSecPreSubmit.doc

---

### Post by mak123 on 2007-08-23
> **Acglaphotis said:**
> i ment opening a terminal (applications>accesories>Terminal and doing these commands)

```

cd /media/Sansagoeshere/

```

when you are there do a 

```

ls

```

That should list all of the files in the directory. If that doesnt work type

```


gksudo nautilus /media/Sansagoeshere


```

Then pressing Control+H. If that doesnt work try it on another computer and see f the problem persist.

Sorry about not being clear enough in my first post : ).

EDIT:Im going to sleep. I'll be back in 12 hours.

I think I should just reset/reformat my MP3 player.

Is there a way to do that even though I can't get it to work right?

(I couldn't find anything through Sansa or Google.  Maybe I missed something...)

Thanks.

---

