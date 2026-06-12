---
title: "Oddity with Firefox 2"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by anothernewuser on 2007-02-15
So ... .I'm very new to ubuntu and I was quite happy with myself when I found the way to upgrade to the new firefox version (i chose to follow some advice I linked to out of this forum and downloaded "installnewfirefox.sh" which worked out fine!).  But it's raised a few questions which I'd really appreciate some info about.

1. Why is it that the "check for updates" option is greyed out?

2. Related to the above, how would I get updates to Firefox 2?  Will the update manager still dowload changes or will I have to do it manually?

3.  I set up firefox to default to google home page for simplicity and quick starting up.  But ... anything related to [www.google.com](www.google.com) seems to get crossed up with the bbc website.  The URL shows as "http://www.google.com" but there's clearly a bbc page underneath and when I do any websearch through google i get a bbc error page.   Regional google sites seem to be working okay.  Anyone know whta's up or how to deal with it?


Any advice would be much appreciated.

Thx.

---

### Post by moshuptrail on 2007-02-15
1. Just guessing...  Something in setup.  Maybe a web-site needs to be configured...

2. You won't get updates through synaptic.  Synaptic only looks to the Repos listed in Synaptic.  

3. Sounds like the search engine list is bad.  I'm not sure where you'd find that.  What happens if you change your default seach engine to Yahoo?

---

### Post by Bachstelze on 2007-02-15
1) Because Firefox is not running as root.

2) If running Dapper, [here](http://psychocats.net/ubuntu/firefox) you go. If you have done that already, here's how to use the auto-updating feature of firefox. First, you need to run firefox as rood, open a terminal and run *gksudo firefox*, you will be prompter for your password and then firefox will run, letting you autoupdate it. When the update is done, *don't* choose to restart ff automatically. Close it yourself, restart it with *gksudo* to complete the update then close it again and you can run it normally thenceforth.

3) No idea, sorry, Google works fine for me.

---

### Post by anothernewuser on 2007-02-15
Thx for your advice.

Yahoo works fine.

"firefox is not running as root" ... how do i fix that?

---

### Post by moshuptrail on 2007-02-15
1. If you click on Preferences, then the Advanced Tab, then help you can find this note:

```
Note:  You must be running Firefox as an administrator root or as the user who originally installed Firefox to install Firefox updates.

```

Start a Terminal, then type gksudo firefox

Then check!

P.S. Don't do any browsing like this.  Its very dangerous.

---

### Post by anothernewuser on 2007-02-15
When I click on Preferences, Advanced I don't get that message.  I get through to the next screen. I can check for firefox to get updates to add-ons and search engines but not to itself.

I think I may have download the Mozilla version which someone said is "self-updating" ... does that mean i need never update it?


Sorry ... read your post again.  Give me a minute.

Ok ... i found this entry in the help:

Automatically check for updates to:

      By default Firefox automatically checks for updates to itself, to
      add-ons, and to search engines so you'll always know you have the most
      up-to-date version. You can change this behavior by changing the
      appropriate checkboxes here.

But what concerns me is the "Firefox" update option is greyed out I can't turn it on our off.  If that's supposed to be like that then it's ok.


Thx to both of you for your advice.  I have to run now but will check back here later.

---

### Post by Bachstelze on 2007-02-15
> **HymnToLife said:**
> 
2) If running Dapper, [here](http://psychocats.net/ubuntu/firefox) you go. If you have done that already, here's how to use the auto-updating feature of firefox. First, you need to run firefox as root, open a terminal and run *gksudo firefox*, you will be prompted for your password and then firefox will run, letting you autoupdate it, don't do any browsing like this. When the update is done, *don't* choose to restart ff automatically. Close it yourself, restart it with *gksudo* to complete the update then close it again and you can run it normally thenceforth.

Added that afterwards ;)

---

### Post by anothernewuser on 2007-02-16
oki doki,

I begin to understand what you mean.  I followed your instructions and was indeed able to check for updates.

I'm still baffled by why I get the bbc when i try to use google but thx for your help.

That's a nice little baby step forward in understanding.  I'll save my next questions for tomorrow.

---

