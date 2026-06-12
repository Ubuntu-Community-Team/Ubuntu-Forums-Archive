---
title: "[SOLVED] Xubuntu Terminal launcher error"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jesusfreak107 on 2008-01-21
I just installed Xubuntu 7.10 Gutsy Gibbon. ( a couple of hours ago ).  However, every time I try to open the terminal, it simply logs me out of my account, and does nothing.  This is the first time I have used Xubuntu, I have been using plain Unbuntu, but my slower machine did not like it, so I decided to try Xubuntu.  Is this a normal occurrence, am I supposed to do something else, or is this a bug? Thanks.

---

### Post by emarkd on 2008-01-21
I had a similar problem when I tried Xubuntu a while back.  I just circumvented the problem by installing xterm and using that instead.  I'm no longer using Xubuntu so I never found a better solution.

Hope this helps a little...

---

### Post by jesusfreak107 on 2008-01-21
I checked the synaptic package manager, and apparently, that is the one I am using.  must be a bug in a recent update of it. I'll install the normal Terminal, and see if that works. 
Thanks!

---

### Post by emarkd on 2008-01-21
The standard Ubuntu "Terminal" app is actually gnome-terminal.  You may have both installed but your menu shortcut for "Terminal" may actually point to gnome-terminal.  Try hitting <ALT>F2 and running 'xterm'

---

### Post by jesusfreak107 on 2008-01-21
HAHA! thank you! now... how do I add a launcher that points to the correct one? I'll try, but specific instructions are always useful.

---

### Post by emarkd on 2008-01-21
Can you right-click on the menu bar and select "Edit Menus"?  It's been a while since I used Xubuntu so I don't remember.  If that doesn't work, the menu editor is (I think) called alacarte, so you could just run it from xterm or from the <ALT>F2 box and edit your menu item from there

---

### Post by jesusfreak107 on 2008-01-21
THANK YOU FOR YOUR HELP! I was able to solve my problem way faster than I ever considered possible! the problem is solved, thanks to you.

---

### Post by emarkd on 2008-01-21
You're quite welcome.  One of Ubuntu's biggest assets is it's community.  I've benefited from it myself many times.  I'm glad I could help.

---

