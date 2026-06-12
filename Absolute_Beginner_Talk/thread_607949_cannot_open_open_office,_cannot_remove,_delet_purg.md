---
title: "cannot open open office, cannot remove, delet purge it either"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-11-09
I keep getting the auto recovery screen when I try to open any ooo stuff..

no files are listed to be recovered and when i hit close or cancel or OK it starts all over again.

I after this I cannot get the computer to shut down, no force quite.. I have to hold down teh power button for 5 seconds.


I tried removing it in terminal  and it seems to have worked but when I look at applications - office they are still listed there and give me the same problems.

so does this mean I have not removed it?

If I use add/remove when i click to remove the check mark next to any ooo apps i get an error msg saying I cannot remove it.

I really need a spread sheet pgr and a word processor. abiword is fine but I have ooo at work so I would like to stick with it.

robi

---

### Post by FuturePilot on 2007-11-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/131526](https://bugs.launchpad.net/bugs/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Sounds like this bug.^
Try either switching to the Human theme or remove openoffice.org-gtk
```
sudo apt-get remove openoffice.org-gtk
```

---

### Post by beanco on 2007-11-09
> **FuturePilot said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/131526](https://bugs.launchpad.net/bugs/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Sounds like this bug.^
Try either switching to the Human theme or remove openoffice.org-gtk
```
sudo apt-get remove openoffice.org-gtk
```

as far as I know I am still using Human Theme... but I will check again... and as far as the code goes, that is what I did but it did not help.

robi

---

### Post by beanco on 2007-11-09
I tried it again, rebooted and they are still there in applications - office


robi

ps I am on feisty for what that's worth.

---

### Post by FuturePilot on 2007-11-09
> **beanco said:**
> I tried it again, rebooted and they are still there in applications - office


robi

ps I am on feisty for what that's worth.

That command won't remove OpenOffice, just the Gtk integration package. But it won't help as that bug doesn't affect Feisty.
Maybe the settings are corrupt.
Try
```
mv ~/.openoffice.org2 ~/.openoffice.org2_old
```

---

### Post by beanco on 2007-11-09
> **FuturePilot said:**
> That command won't remove OpenOffice, just the Gtk integration package. But it won't help as that bug doesn't affect Feisty.
Maybe the settings are corrupt.
Try
```
mv ~/.openoffice.org2 ~/.openoffice.org2_old
```


OK, I am too much a noob to follow this.

I went to terminal and pasted in your command.

then what should I do?

Robi

---

### Post by FuturePilot on 2007-11-09
> **beanco said:**
> OK, I am too much a noob to follow this.

I went to terminal and pasted in your command.

then what should I do?

Robi

Sorry, should have explained this more. ;) Hit Enter after putting it in a terminal, then try to start Open Office again.

---

### Post by beanco on 2007-11-09
> **FuturePilot said:**
> Sorry, should have explained this more. ;) Hit Enter after putting it in a terminal, then try to start Open Office again.

that's what I did and nothing happened! I mean no changes.

Robi

---

### Post by FuturePilot on 2007-11-09
So it's still giving you the recover document thing?

---

### Post by beanco on 2007-11-09
> **FuturePilot said:**
> So it's still giving you the recover document thing?



yeap!


if I try to uninstall remove it I am told it is not installed.

if I try to install it I am told it is installed already...

very weird

robi

---

### Post by skyjacker on 2007-11-09
you might want to try the koffice tools. kspreadsheet handles oo spreadsheets, and I have found it to be a little better than oo because when you save a file, it automatically makes a backup copy. it does everything oo can do. Get it from the repos.:)

---

### Post by beanco on 2007-11-10
skyjacker, thanks!

got it installed.. i will look through the word processor and the spred sheet thing.

I hope they can both handles several languages and have decent spell checks.

not really in teh mood to learn how to tweak new prgms to meet my needs but I am in a bind..

I would still like to get the open office issue resolved. so if anybody has any ideas, let me know.

robi

---

### Post by beanco on 2007-11-10
i forgot to ask

cna the koffice files be read in MS?

Major part of my business is sending translations to clients and they all us MS!!!! They lazy and unwilling to deal with anything that is more work than click once to open.


robi

---

### Post by beanco on 2007-11-10
OK, I am about to give up!

I got rid of open office completely using synaptic.

 why was this no possible using terminal


However, I cannot use it. I get the same old freaking problem. I mean, I reinstalled it using add/remove and it will not work. Now I will remove it again with synaptic.

and try on last time.

Robi

---

### Post by beanco on 2007-12-21
been using koffice, andit is fine. but it does not have character/word count... this is important for my work.

robi

---

