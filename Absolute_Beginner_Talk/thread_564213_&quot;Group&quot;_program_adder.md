---
title: "&quot;Group&quot; program adder"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-09-30
[SIZE=3]I've just finished my script for adding a bunch of programs as a group (version 1.3.1 now) - I think this will be really useful for people after a fresh installation needing a ton of stuff **now**! :p

You can find it attached - it's not graphical like the RAR maker, but it's just as easy to use, and technical knowledge is not necessary!  Simply pick a category, it will list what it plans to install, and then you can pick yes or no.  After it's done, you can choose to keep going, or leave.  Tell me what you think!

Thanks to Frak for some minor fixes :p

[/SIZE][COLOR=DarkRed]**License:**
-You MAY download and do whatever you want to the script, under the terms below:
-You may NOT redistribute it in any way for any reason without my permission (but chances are good you'll get a yes )[/COLOR]
 A similar project I think I should draw attention to is [*HERE*]("http://ubuntuforums.org/showthread.php?t=562538").  There's some really good work going into it! ;)

---

### Post by Frak on 2007-09-30
You may want to add your license.

EDIT
You may also want to warn people to run this with the prefix bash
```
bash <location/of/script>
```

---

### Post by ryanVickers on 2007-09-30
> **Frak said:**
> ...You may also want to warn people to run this with the prefix bash
```
bash <location/of/script>
```

Why would I do that?

---

### Post by Frak on 2007-09-30
> **ryanVickers said:**
> Why would I do that?
If you run it under the terminal, you have to specify the shell.

I also added a fixed script, some of your commands were named spt-get instead of apt-get, and I also added a -y flag to each command.

---

### Post by ryanVickers on 2007-09-30
> **Frak said:**
> If you run it under the terminal, you have to specify the shell.

I also added a fixed script, some of your commands were named spt-get instead of apt-get, and I also added a -y flag to each command.

ok, I updated the first post to use this one :)

but still, If I have #!/bin/bash in the first line, why should I need to do that other thing you said?:confused:

---

### Post by Frak on 2007-09-30
> **ryanVickers said:**
> ok, I updated the first post to use this one :)

but still, If I have #!/bin/bash in the first line, why should I need to do that other thing you said?:confused:
Yes, that does specify the shell if executed. But since running from the CLI is bash, it will require the user to enter a program, and then an operator, flag, option, or input.

So, instead of entering the /path/to/the/program.bin_or_script.sh, the user would have to enter bash /path/to/the/program.bin_or_script.sh

Clear as mud?

---

### Post by ryanVickers on 2007-09-30
All make sense now, is clear as toast! *with Swedish accent* :p (don't ask, it's from a show :))

---

### Post by Frak on 2007-10-07
Some great improvements. I prefer this over automatix now for a number of reasons.

---

### Post by ryanVickers on 2007-10-07
It's in no way designed to be able to measure up to automatix because it just uses the default repos (I think for the most part), but it is nice for people after a fresh install who need a ton of stuff like NOW! :p

---

### Post by Frak on 2007-10-07
> **ryanVickers said:**
> It's in no way designed to be able to measure up to automatix because it just uses the default repos (I think for the most part), but it is nice for people after a fresh install who need a ton of stuff like NOW! :p
The new automatix isn't out yet and the last one always installed from the repo's anyways exept for Swiftfox and Opera I believe.

But this much easier and faster for me, just because I would rather batch install from the CLi then slowly select different packages.

---

### Post by ryanVickers on 2007-10-07
Well, I guess as long as someone likes it :p

---

### Post by aktiwers on 2007-10-16
Love it! Thanks! :)

---

