---
title: "Web Browsers With Orca"
date: 2006-11-06
forum: Assistive Technology &amp; Accessibility
---

### Post by Pipistrelle on 2006-11-06
I'm using the live cD of Ubuntu 6.10, and I'm very happy with most of the accessibility aspects. I've noticed that Epiphany works relatively better than the current Firefox, and I'm looking forward to future Firefox accessibility.

A question occurs to me: is there a way to make Orca work with text browsers, if, for example, it runs from root? I've tried it in a terminal, but it doesn't read the highlighting, etc.

Keep up the good work, all. I'm excited about the new Orca.

Teresa

---

### Post by kd7swh on 2006-11-06
In firefox you can use the keyboard to navigate pages if you do this:

Edit > Preferences > Advanced > General > Always cursor keys to navigate within pages [ check this ]

This makes orca a little more functional.

As for the text browsers, try w3m. I haven't had any problems running orca with text browsers.

running as root is something you can try:

(sudo orca; w3m)

but I don't see what difference this would make.

Just keep playing with different browsers. You might find that lynx or links works better for you.

Post your findings, and let us know what works best for you.

---

### Post by Pipistrelle on 2006-11-06
Well, unfortunately, changing the keyboard options in Firefox accessibility preferences doesn't seem to make a difference. Orca reads the element names most of the time on tab- and arrow-key presses, and may or may not read any text after reading these labels. Epiphany does this to a lesser extent.

Oddly enough, epiphany seems to work much better at the moment, though image tags are still not read.

I tried loading a text-based web browser--actually several, and got no useful results. I tried in a terminal and in the console. Orca doesn't speak the highlighted text in elinks, (I downloaded this with add/remove) and I got an error message with w3m, the last three words of which were: "Do not use." Then I was unceremoniously thrown back into the shell prompt. Links ( with a k) apparently isn't included, nor is lynx (with an x) , but I may try the former. So I think I'm going to wait till I have a reliable web-browser that reads tags and works with multimedia before I actually install. I'm seriously considering doing this, however, as I'm happy with Orca in general.

Thanks,
Teresa

---

### Post by Pipistrelle on 2006-11-06
Ahem! I was using speech and didn't notice the semicolon in a command-line option posted here. I'm going to go try it again ...

Teresa

---

### Post by Pipistrelle on 2006-11-06
Well, I'm following up on myselves a lot; sorry, but just reporting that I'm having no luck at all with any text browser thus far and I'll expect to play with Epiphany until Firefox (3?) comes out.

Thanks,
Teresa

---

### Post by leenac on 2009-12-15
Our team is working on Accessibility issues with computer usability.
we are new to use orca and using it with ubuntu 9.01 and FF 3.0. As we found Orca works fine with many applications like search for a file desktop frames and many more.

[B]Basic question is How screan reader workes with web page? 
[/B]We have explored orca with Firefox and got following issues with web browser:

[LIST]
[*]Orca is     expected to provide list of visited/unvisited link(but can visit     link by v/u as listed in table), list of combo boxes, list of action     buttons etc.
[*]What are the     keyboard shortcuts To navigate (some of them are listed in Gnome site but they are not working)
[LIST]
[*]Web page         form  (to work with HTML form)
[*]HTML Frames
[*]      HTML Tables
[/LIST]
 
[/LIST]
[B]With mail engines: 
[/B]

[LIST]
[*]How to shift      and read next frame in mail site like yahoomail .co.in. Does Orca     has any command to do this, like jaws has M and shift+M). this is     required to read directely list of mails in inbox, so that we can     select mail to read or to perform any actionlike /reply/forward/...
[*]What are the KB shortcut to     perform action on mail site like Compose mail/Delete mail, move     mail...
[*]How to     perform following basic operations:
[LIST]
[*]send e-mail
[*]reading mail
[*]quick reply
[*]attachments
[*]contacts,     search, deleting
[*]marking msg
[*]move to
[*]label.............
[/LIST]
 
[/LIST]
Your suggestions in this regard will be help full for further exploration and study.

thanks

---

### Post by GraysonPeddie on 2009-12-19
Woah! Why post in such an old thread dated back to 2006?

Your post doesn't seem to be related...

---

