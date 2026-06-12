---
title: "Game Graphics Problems"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Annigma on 2007-04-27
Hello. I've got 7.04 up and running and so far so good.. :)

There's a game called 'PlaneShift' which I thought I'd try and get up and running. Download and install went well. The game console opened up but the writing was unreadable. I fixed this with a nice link that told me how to change a simple command in the .cfg file of the game. Now that part is fine.

The problem I am now having is that the character/avatar doesn't appear, and if I go into the game, I see.. nothing pretty much: just the chat window and a few other 'non-3D-graphics' things..
I've followed a few links about installing ATI graphics drivers, but I don't know whether I should do this: I don't want to make things worse.. Currently, music files play nicely, a video clip played perfectly, and everything seems 'hunky dory', so I don't want to break it!

I would appreciate some advice on this matter. I am a complete Linux novice, so please bear in mind that console commands, etc. are not yet very familiar to me ;) (there seem to be many helpful people 'out there', though most assume some previous Linux knowledge :o).

I'm on an Athlon XP-something (2700?) and my graphics card is a Sapphire Radeon Pro 9700.

Thank you.

^..^

---

### Post by paparucino on 2007-04-27
> **Annigma said:**
> 

I'm on an Athlon XP-something (2700?) and my graphics card is a Sapphire Radeon Pro 9700.


May be you haven't the 3D support installed

Try this 

```

http://doc.gwos.org/index.php/ATI_AMD_fglrx_Edgy

```

even if it's for Edgy, it should work for Feisty

---

### Post by WHICKS on 2007-04-27
If you are running under Beryl, some of the games won't run well if at all.  Switch back to the gnome desktop and that made a huge difference to my ability to run 3d games

---

### Post by Annigma on 2007-04-27
Thanks for the responses.
Jumping ahead to Step 2 in that link paparucino, I see something I almost did already, only a more recent driver. Looking [here, at the ATI/AMD site]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") I am unsure about this:
"Notes:
The above drivers support English only.
[b]The display driver requires POSIX shared memory to be enabled on the system.
Kernel Source package is no longer required if Kernel Header package is installed.[/b]"

How do I check whether 'POSIX shared memory', and 'Kernel Header package' are enabled on my system?

This is quite a long series of steps to follow. I don't have a problem with that, however:

Is it safe?
Can I 'break' my computer doing this?
Can I revert if it doesn't work? (like Windows' 'System Restore' or something..)

I don't believe I am using Beryl: I certainly haven't installed it. Beryl is some kind of 3D enhancing thing isn't it..? I prefer Gnomes ^..^

:)

---

### Post by paparucino on 2007-04-27
> **Annigma said:**
> Thanks for the responses.

How do I check whether 'POSIX shared memory', and 'Kernel Header package' are enabled on my system?

Really don't know. It's a guru argument :-)
Yuou could ask on IRC channel #ubuntu on freenode

> 
Is it safe?
Can I 'break' my computer doing this?
Can I revert if it doesn't work? (like Windows' 'System Restore' or something..)

In a no way you damage your computer.
If you have another partition you can backup your sistem
> 
I don't believe I am using Beryl: I certainly haven't installed it. Beryl is some kind of 3D enhancing thing isn't it..? I prefer Gnomes ^..^

Beryl is not automagically installed since it is again in beta state.

---

