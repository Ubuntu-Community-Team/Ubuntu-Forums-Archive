---
title: "how do i run a process in background?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-12-07
I connect my server often using an ssh session kind of often.
Sometimes i need to trigger stuff that will take a few minutes or hours to execute, like wget donloads and stuff.

How do i run a process in background so when i close the conenection with the local computer the process keeps its execution until the end?

---

### Post by taurus on 2006-12-07
You would put the "nohup" in front of the process.

```
man nohup
```

---

### Post by CatKiller on 2006-12-07
I would use **screen**.

---

### Post by weresheep on 2006-12-07
Yup, screen is what you want to use.

Here are the basics (I've only started to use it myself).

After you login to your machine via SSH run the 'screen' program. I can't remember if its installed by default but "sudo apt-get install screen" should work if it isn't. With screen running the shell looks like normal and you can use it like normal. When it comes time to logout, hit 'Ctrl a' followed by 'Ctrl d'. Thats the control key with lower case a, followed by the control key and lower case d. You should then see a message saying "[detached]". What ever program(s) you were running before are still running, only you can't see them at the moment. 

To reconnect to the programs run "screen -r". Everything should now be back where you left it.

So you can...

1)  SSH into machine
2)  Run 'screen'
3)  Do stuff (e.g. start long running command)
4)  'Ctrl a' 'Ctrl d' (detach)
5)  Logout
...
6)  SSH into machine
7)  Run 'screen -r'
8)  See if command from 3) is finished, do more stuff

If you are fully finished with screen, use 'exit' to get yourself back to a plain shell.


The screen program can also let you run multiple programs at the same time from within one shell. Whilst running screen, if you hit 'Ctrl a' then 'Ctrl c' you get a fresh prompt. You can use this prompt as normal. If you want to go back to the first command prompt, which is still doing what ever you left it doing, hit 'Ctrl a' then Ctrl a'. To get back to the second prompt again hit 'Ctrl a' then Ctrl a' a second time.

Ctrl a, Ctrl a jumps between the last two command prompts that you used. However you can have more than two running at the same time and so you can also use 'Ctrl a' then N (e.g. 0, 1, 2 etc) to jump to a prompt directly. So to get back to the first prompt hit 'Ctrl a' then 0. The second is 'Ctrl a' then 1 and so forth.

If you have more than one 'screen' prompt open, then typing exit only quits the current prompt, not 'screen' itself. So you have to exit multiple times before screen itself will quit.

Hope that helps. Check out the screen man page to get more detail.

-weresheep

---

### Post by pedrotuga on 2006-12-07
Thank you very much everybody.

---

### Post by anaconda on 2006-12-07
how about just running the processes in background using "&"

eg:
```
nautilus &
```
would start nautilus on the background...

---

### Post by Bachstelze on 2006-12-07
Because then the process will be terminated if you log out/

---

### Post by Monsieur le Comte on 2007-01-18
Thanks everyone! I haven't had to resume yet, but this is a kick-butt program!

---

