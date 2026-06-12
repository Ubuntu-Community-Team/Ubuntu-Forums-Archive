---
title: "Why does copy/paste not work for Evolution?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by stig on 2006-06-14
Hi,
I'm using Evolution 2.6.1 on Ubuntu 6.06.
I have problems copying and pasting text from elsewhere into new email messages.

1. If I copy a sentence of text from a web page in Firefox and paste it in the message, the resulting text sometimes appears to have retained formatting from the web page. It doesn't look different from typed text in the message but the cursor becomes larger and I can't fully edit the text. In other software like OOo an obvious answer would be to use Paste Special but Evolution seems not to have this function. How can I avoid the problem and get simple unformatted text?

2. If I try to copy text from a received or a sent message and paste it into a new message nothing is inserted. I've tried using Edit/Copy, Ctrl C, right-click Copy but with no success. What am I missing here? I understand you can use the middle mouse button but I don't use this in any of the other applications I work with and it doesn't seem to work reliably in Evolution. Copy/paste the "normal" way works OK in Thunderbird on my PC.

---

### Post by morequarky on 2006-06-14
I don't know why.

Try draging text.

---

### Post by stig on 2006-06-14
[QUOTE=morequarky]Try draging text.[/QUOTE]

Not very convenient compared with the usual methods.

What makes the problem seem more odd is that sometimes the normal copy/paste
works - but I can't find any reason for why it works sometimes, not others.

---

### Post by rplantz on 2006-06-14
[QUOTE=stig]Hi,
I'm using Evolution 2.6.1 on Ubuntu 6.06.
I have problems copying and pasting text from elsewhere into new email messages.

1. If I copy a sentence of text from a web page in Firefox and paste it in the message, the resulting text sometimes appears to have retained formatting from the web page. It doesn't look different from typed text in the message but the cursor becomes larger and I can't fully edit the text. In other software like OOo an obvious answer would be to use Paste Special but Evolution seems not to have this function. How can I avoid the problem and get simple unformatted text?
[/quote]
There is  a row of text formatting icons just above the compose are. The one labeled "TT" will "Toggle typewriter font style."
> 
2. If I try to copy text from a received or a sent message and paste it into a new message nothing is inserted. I've tried using Edit/Copy, Ctrl C, right-click Copy but with no success. What am I missing here? I understand you can use the middle mouse button but I don't use this in any of the other applications I work with and it doesn't seem to work reliably in Evolution. Copy/paste the "normal" way works OK in Thunderbird on my PC.
The only way I have found to do this is to "Reply" to the message and copy the text I want. Then I cancel my "Reply." I do not like having to go through these additional steps. I understand that the received message should be read only, but I should be able to copy from it directly.

---

### Post by stig on 2006-06-14
[QUOTE=rplantz]There is  a row of text formatting icons just above the compose are. The one labeled "TT" will "Toggle typewriter font style."[/QUOTE]

These icons are greyed out and don't work. I've tried them when text is highlighted but still they are greyed out.

[QUOTE=rplantz]The only way I have found to do this is to "Reply" to the message and copy the text I want. Then I cancel my "Reply." I do not like having to go through these additional steps. I understand that the received message should be read only, but I should be able to copy from it directly.[/QUOTE]

Yes, I don't like having to do such extra steps. I don't understand why Evolution has File/Edit/Copy if the word "Copy" is greyed out and not useable.

---

### Post by rplantz on 2006-06-14
[QUOTE=stig]These icons are greyed out and don't work. I've tried them when text is highlighted but still they are greyed out.[/QUOTE]

Go to Edit->Preferences and click on the Composer Preferences. Select Format messages in HTML.

I'm still not sure if this works the way I think it should. Namely, I, and apparently you, would like to be able to copy some text from a web page and paste it into an email message as plain text.

Sometimes I pine (pun for oldtimers) for the old days of command lines and text only computing.

---

### Post by bruce89 on 2006-06-14
It could be Firefox not being a proper GTK+ application.

---

### Post by mjm115 on 2006-06-14
It looks like there may be a problem with your choice of Mail Format for you messages.

---

### Post by stig on 2006-06-15
[QUOTE=rplantz]Go to Edit->Preferences and click on the Composer Preferences. Select Format messages in HTML.

I'm still not sure if this works the way I think it should. Namely, I, and apparently you, would like to be able to copy some text from a web page and paste it into an email message as plain text.

Sometimes I pine (pun for oldtimers) for the old days of command lines and text only computing.[/QUOTE]

You're right - I don't like writing messages in HTML, especially because some of my contacts and customers may not want HTML messages. I guess at 59 I'm an old-timer and, although I don't pine for the command line I do find it strange that my old applications on Win98 often seem to have more useful features than "modern" software!

I asked the same question about copy/paste on the Evolution mailing list several days ago but still have not had a reply. I'm now running Thunderbird alongside and probably will change.

Thanks for the moral support!

---

### Post by Sweezel on 2006-06-16
Yes, it really does suck...

Sometimes it works and sometimes it doesn't. 

This is my worst nightmare in Ubuntu.

---

### Post by stig on 2006-06-19
I "solved" my problem with Evolution by switching to Thunderbird. After running them side-by-side for a few days I exported my address directory to Thunderbird and copied all my email to Thunderbird. No problems so far! I don't need any of the other Calendar, Tasks etc functions so this suits me fine.

---

