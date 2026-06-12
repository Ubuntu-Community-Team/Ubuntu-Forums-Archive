---
title: "Refreshing terminal prompt?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Patto77 on 2008-01-10
Sometimes after running a command in the terminal window it fails to return to the myname@myname-desktp:~$ prompt.  I then have to either close and re-open the terminal or open a new tab.

Is there a simpler way to refresh the terminal?

---

### Post by Rocket2DMn on 2008-01-10
Sometimes just clicking enter gets you back to a prompt, otherwise ctrl+c kills the current process that you previously typed in and gives you your prompt back.
To run programs in the background, complete the command with the "&" sign.

---

### Post by Patto77 on 2008-01-10
I'll give that a go.  Thanks.

---

### Post by Joeb454 on 2008-01-10
Like Rocket2DMn said, if you wanted to run a process separately from the terminal, such as rhythmbox for example, I would type ```
(rhythmbox &)
``` and then carry on my terminal work :)

---

### Post by erginemr on 2008-01-10
> **Patto77 said:**
> Sometimes after running a command in the terminal window it fails to return to the myname@myname-desktp:~$ prompt.  I then have to either close and re-open the terminal or open a new tab.

Is there a simpler way to refresh the terminal?

If this is what you are referring to, sometimes you lose the terminal, say after trying to list the contents of a binary file, filling up the screen with garbage. In such cases, issuing the command "reset", even if you cannot see the letters as you type, will bring back your terminal screen.

Speaking of screen, there is a marvellous command installed by default which is called "screen", which allows you to run commands on one virtual screen and continue to work on another. It takes some time to get used to, but does wonders once you get the hang of it.

---

