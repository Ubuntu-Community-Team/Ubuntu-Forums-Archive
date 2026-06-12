---
title: "Folders Not Opening in Terminal"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by slickidiotfan on 2007-04-15
I have tried both the gnome-terminal and the xterminal but when I open a directory I try "Open with Terminal" and it shows a tab at the bottom that says "Opening 'folder'" and it doesn't open with the terminal. Anyone know the solution?

---

### Post by thelinuxguy on 2007-04-15
> **slickidiotfan said:**
> I have tried both the gnome-terminal and the xterminal but when I open a directory I try "Open with Terminal" and it shows a tab at the bottom that says "Opening 'folder'" and it doesn't open with the terminal. Anyone know the solution?

System >> Administration >> Synaptic Package Manager
Install the package nautilus-open-terminal
Logout and login again
Now when you right click on a folder, you will get a menu item "Open in terminal"

Is this what you were looking for?

---

### Post by slickidiotfan on 2007-04-15
Nope, that didn't do it :-/

---

### Post by thelinuxguy on 2007-04-15
> **slickidiotfan said:**
> Nope, that didn't do it :-/

Could you be a bit more specific? Or maybe reframe your question? I thought you were trying to right click a folder and open a terminal with that folder as its working directory. This works by my post above. But it seems you are trying to achieve something else.

---

### Post by slickidiotfan on 2007-04-15
Nope, I'm trying to do what you are saying. Even after downloading and restarting the nautilus file it still just says "Opening 'Directory'" and doesn't open to the terminal.

---

### Post by WakkiTabakki on 2007-04-15
It's most likely a problem with the script. Try this:
1. Open a terminal
2. Start nautilus from that terminal
3. In nautilus, try opening a terminal with the script and observe the output in the terminal from step 1
(hmmm... did that make sense?)

/N

---

### Post by thelinuxguy on 2007-04-15
> **slickidiotfan said:**
> Even after downloading and restarting the nautilus file it still just says "Opening 'Directory'" and doesn't open to the terminal.

You were getting this error even before installing nautilus-open-terminal. I guess you are trying Open with other application >> gnome-terminal. That's not required and it doesn't work at my end either. 

After installing this package, a new menu item appears when you right click a folder. On my system, its second from bottom. Just above Properties. Just clicking it opens a terminal in that folder. No additional steps are necessary.

---

### Post by thelinuxguy on 2007-04-15
Here is another way:
[LIST=1]
[*]Navigate to .gnome2/nautilus-scripts within your home folder
```

cd ~/.gnome2/nautilus-scripts

```
[*]Create a new text file (say Terminal) there and put the following lines in it
```

#!/bin/bash
gnome-terminal

```
[*]Grant execute permissions on the file
```

chmod +x Terminal

```
[*]Now when you are within a folder, right click in the folder and select Scripts >> Terminal. This should open a terminal in that folder.
[/LIST]

The only difference is that you can't right click on a folder's icon and open a terminal there. You have to open the folder first to do this. 
Does this work for you?

We could modify the script so that we don't need to open the folder first to get a terminal there. I couldn't get it working and would be interested to know the solution.

---

### Post by slickidiotfan on 2007-04-15
> **thelinuxguy said:**
> You were getting this error even before installing nautilus-open-terminal. I guess you are trying Open with other application >> gnome-terminal. That's not required and it doesn't work at my end either. 

After installing this package, a new menu item appears when you right click a folder. On my system, its second from bottom. Just above Properties. Just clicking it opens a terminal in that folder. No additional steps are necessary.

That was it #-o! I feel so stupid because I was doing it earlier today...Thanks guys.

---

### Post by thelinuxguy on 2007-04-16
> **slickidiotfan said:**
> That was it

Good to know that you finally have it working at your end. This has raised a question in my mind. Referring to my post above, is there any way a shell script can access what Nautilus would pass to an application/extension registered to start on clicking a menu item in the context menu? This data doesn't seem to be accessible to the script via positional parameters. Any ideas?

---

### Post by thelinuxguy on 2007-04-16
Looked like a programming question. Have created a new thread at [http://ubuntuforums.org/showthread.php?p=2462083#post2462083](http://ubuntuforums.org/showthread.php?p=2462083#post2462083)

---

