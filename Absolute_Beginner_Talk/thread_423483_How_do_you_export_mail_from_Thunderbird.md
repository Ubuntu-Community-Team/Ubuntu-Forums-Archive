---
title: "How do you export mail from Thunderbird"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-25
I'm getting rid of Linux, at least for the time being (maybe a long time, maybe a short time) and I'd like to export my mail from Thunderbird. I couldn't find an export function. It there one?

If not I guess I'll have to forward them to myself.

---

### Post by Lucifiel on 2007-04-25
Oh, go into /home/<user> where <user> = your current username.

Click Ctrl + H to show hidden files and go to .mozilla-thunderbird. Then, just copy your "plkbndex.default" or whatever your profile folder is named, to another partition.

---

### Post by alienexplorers on 2007-04-25
You could save your mail in .eml format and if running Thunderbird in Windows or whatever you could then import them back into thunderbird.  I do this between linux and my windows computer.

---

### Post by aysiu on 2007-04-25
You could copy your profile from /home/username/.mozilla-thunderbird if you're using Ubuntu's version of Thunderbird (or ~/.thunderbird if you're using Mozilla's version of Thunderbird) to C:\Documents and Settings\username\Application Data\Thunderbird

---

### Post by bliffle on 2007-12-05
I'm reviving this because I want to export my thunderbird database from my old ubuntu computer to my new ubuntu computer.

I tried copying/moveing the "thunderbird" and ".thunderbird" folders from the old comp to the new comp , but when I bring up T'bird it doesn't see them.

Maybe I have the Mozilla version of tbird on the old comp and the gnome version of tbird on the new one, because I used Synaptic to dl/install tbird on the new comp just a few minutes ago. I think that makes a difference.

If I can't figure anything else out I'll delete the synaptics tbird from the new comp and apply the mozilla version and try agaIN.

---

### Post by HermanAB on 2007-12-05
Howto move Tbird mail:
1. Quit Tbird
2. Find the correct location of the mail files
3. Copy the mail files over from the old location (You only really need 'Inbox' and 'Sent' and can delete everything else).
4. Start Tbird

Cheers,

Herman

---

### Post by bliffle on 2007-12-06
I think I need more.

When I moved my email from  XP Outlook Express I first moved to XP Thunderbird, then I exported again and moved to ubuntu Thunderbird and it worked perfectly! I kept all my folders and boxes, AND I kept my accounts, which are several. Very nice. Very little touchup was required on the target ubuntu system. So I am certain there is a way to export everything (even the accounts) from one ubuntu system and put it on another.

But I am coming to believe that the 2 ubuntu Tbirds must BOTH be either Mozilla or Gnome originated. So that would mean I must un-install the Synaptics Tbird from the new computer and install a Tbird from Mozilla in it's place. I have no idea why they would be so different.

---

