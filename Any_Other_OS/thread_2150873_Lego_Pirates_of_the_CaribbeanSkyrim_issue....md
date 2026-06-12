---
title: "Lego Pirates of the Caribbean/Skyrim issue..."
date: 2013-06-02
forum: Any Other OS
---

### Post by DarkJudge on 2013-06-02
I'm running WINE 1.5.31 on Mint 14 (64 bit) GNOME desktop. I am very much a newbie to WINE and Linux in general. The situation is that both games run, both games don't seem to have sound. For the record, I have tried using winetricks xact, vcrun2008 and d3dx9_42. But this did not seem to resolve the issue. I have uninstalled, reinstalled and I have flushed Wine completely and started over. Nothing seems to be working. Does anyone have any ideas as to what I'm doing wrong? I'm expecting that I probably made a stupid mistake somewhere. So, a couple of questions:

1. I presume that you override a dll by providing a name in the GUI or by doing "winetricks <dllname>" (i.e. winetricks xact should cause the xact.dll to override and impliment natively.) Is this correct or did I misunderstand?

2. Does this have anything to do with 32 bit vs 64 bit OS? If so, how do I tell Wine for this game that I only want to run it as a 32 bit application? Or again, have I misunderstood the fundamentals of what I'm trying to do?

Any advice would be appreciated. Let me know if more details are needed. (Yes, I've been through the database. The only test case I could find was someone that got it to work out of box. I know there are problems with the demo with xact, and that's part of the reason I suspect this is the issue, but I'm not positive I've implimented it correctly. FYI, when I type "winetricks xact" from the terminal I received the following message:
"Executing w_do_call xact
xact already installed, skipping"

Which, to me indicates it's already there.

---

### Post by DarkJudge on 2013-06-02
I should probably clarify that Mint is an Ubuntu varient, hence why I'm posting here.

---

### Post by Perfect Storm on 2013-06-03
**Moved to Other OS/Distro Support.**

---

