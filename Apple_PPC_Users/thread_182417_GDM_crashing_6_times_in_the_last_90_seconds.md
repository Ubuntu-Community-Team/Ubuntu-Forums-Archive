---
title: "GDM crashing 6 times in the last 90 seconds"
date: 2006-05-26
forum: Apple PPC Users
---

### Post by RavenOfOdin on 2006-05-26
This is a little strange. . .

I just got done with a bunch of stuff on my iMac and tried to bring up the terminal, through Accessories > Terminal. It didn't work, even after another try. 

Then after pressing Ctrl-Alt-Delete (I had just stopped setting up Miranda IM - on Windows - for my Mom and forgot to substitute Backspace for Delete), the screen displayed a bunch of red lines going vertically down the screen. Two seconds later, it went to a login prompt. I typed in the name of my main account - again that on my PC, by mistake - and the terminal spit at me "Login incorrect."

This is where things get interesting.

The GDM greeter decided to come up on its own and then display a sign at me:

```

The greeter application appears to be crashing. Attempting to use a different one. . .
```

I hit OK, then it went back to the terminal log in prompt. Before I could type my account name in, the GDM greeter came up again and displayed that same sign. OK, type, crash. OK, type, crash. Ad nauseam for about 10 or so more times, after which a blue "default Xserver" screen came up (those ones with the gray background lettering) and said:

```

The display server has shut down about 6 times in the last 90 seconds. It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0

```

Something is obviously wrong at that point, so I use the 2 minute wait to my advantage and log in terminal. Then I type *sudo killall -9 gdm* and restart via /etc/init.d . . .

This works to get me the GDM greeter, and once I get past that, I find myself in my desktop. The console session that wouldn't come up before from Accessories > Terminal is staring me in the face, and right above it is a little error box that says:

```

Error: Failed to initialize HAL!

```

I've only seen that error while running GDM in recovery mode, and as far as I can tell the startup scripts weren't being run during that time period.

Even if I enter the wrong login name in, its a safe bet that the greeter shouldn't be doing this.

What might have caused it? (I recently installed NFS and Apache)

---

### Post by Ptero-4 on 2006-05-26
Are you sure you're running GDM? I see you posted in the kubuntu section, if you're running KDE then you should be running KDM since it's the KDE display manager (GDM is the gnome one).

---

### Post by RavenOfOdin on 2006-05-26
>.<

Can any of y'all say "Oops"?

I probably posted it here 'cause I use KDE on my main box. . .ROFL.

Someone move this to where it should be, please. :D

---

