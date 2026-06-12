---
title: "An Ubuntu Issue or Inkscape Issue"
date: 2011-12-27
forum: Art &amp; Design
---

### Post by Dalian on 2011-12-27
[B]Please HELP me, Wise Ones!
[/B]
I am new to **Ubuntu (using 10.4)** and have installed **Inkscape (0.47)**. When I access it via **Applications/Graphics/Inkscape** it opens up but NONE of the tools work. After browsing user forums I found instructions on how to determine if a root exists for it by entering **sudo inkscape** in the terminal window. This opened the application and I found everything to be in perfect working order. I created and saved a .svg (for reference) to my desktop which appeared with an **svg icon featuring a lock**. I exited the terminal and opened Inkscape once again via **Applications/Graphics/Inkscape** and found the behavior to be the same as I had originally experienced that being no working tools. I would be indebted and greatful to anyone anyone who can help me resolve this issue.

---

### Post by prokoudine on 2011-12-27
Hi Dalian,

I'm afraid I'm going to ask you questions instead of providing answers :)

Is this the first time you ran Inkscape on Linux? If you don;t have any extra Inkscape extensions or Inkscape preferences that are dear to you, what happens if you 'sudo rm -rf ~/.config/inkscape' and try again?

Also, what if you add [this PPA]("https://launchpad.net/~inkscape.dev/+archive/stable") and upgrade to the current version of Inkscape?

Running 'sudo inkscape' is really not recommended. This is exactly why the file you created has a lock icon. It means you created the file with privilefies of the system administrator, and mere mortals don't have access to such files :)

---

### Post by Dalian on 2011-12-28
Prokoudine:

Thank you for the response. Yes it is the first time I have ever used Inkscape in Linux. You see I'm trying to break the Adobe shackles that confine so many in my field. Between the time that I posted and now, I have completely reinstalled Ubuntu on my system, installed updates, and reinstalled inkscape (whereas previously I was downloading via wireless connection I have now down loaded via hardwire) and it works fine now. Thank you very much for your suggestions and help.

---

