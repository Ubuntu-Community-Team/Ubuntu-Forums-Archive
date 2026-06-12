---
title: "Evolution: How to save sent mail in same folder as original msg?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by aridus on 2006-11-16
Could anybody help with this Evolution question please? For most of my mail I prefer to move it to a specific folder before responding. In Outlook I could have the response automatically saved with the original message in the chosen folder (rather than in the Sent messages). Now that I have migrated to Evolution I greatly miss this feature, but cannot see a way of enabling such behaviour. Is there a way of doing this? With grateful thanks...

---

### Post by AlanRogers on 2006-11-16
Good question! Watching this thread with interest ...

---

### Post by jhenager on 2006-11-16
I haven't played with rules in Evolution yet, but knowing how they work in Outlook, I would create two rules.
One to move messages from specific people to the proper folder.
A second to move messages sent to specific people to the proper folder.
[http://www.gnome.org/projects/evolution/doc/evolution26.pdf](http://www.gnome.org/projects/evolution/doc/evolution26.pdf)

---

### Post by aridus on 2006-11-16
Thank you. I have thought of doing this, but I need a more flexible system. The same person may write to my on two or more different subjects and each mail needs to go into a different folder... (and I cannot predict the subject lines to use this in a rule..)...

---

### Post by jhenager on 2006-11-16
> **aridus said:**
> Thank you. I have thought of doing this, but I need a more flexible system. The same person may write to my on two or more different subjects and each mail needs to go into a different folder... (and I cannot predict the subject lines to use this in a rule..)...

I am curious as to how this was done in Outlook.

---

### Post by aridus on 2006-11-16
I don't remember where it is exactly, but it is something you can set in the preferences. The option is labeled something like 'Save replies with original message' or 'Save replies in same folder as original message'.

---

### Post by jimcooncat on 2006-11-16
I have an older Evolution from Breezy, so YMMV.

[INDENT]From the menu, "Edit -> Preferences"

Click tab on left, "Mail Accounts"

In the accounts list, select the account that has "[Default]" in it.

Click the "Edit" button. 

Click the "Defaults" tab at the top of the dialog box.

Click the "Always blind-carbon-copy (bcc) to" checkbox so that it's checked.

Fill in your own email address.[/INDENT]

What this does is to send you a copy of every email you send out. You can then apply a rule to it, where Recipients contains *your-friend@somewhere.com*. That way, all your replies to a particular correspondant get a copy automatically filed. 

Not exactly what you wanted, and you have to make a new rule for every contingency you want handled. But this would work if you have a limited number of cases.

Also, because you're actually sending out a copy, the results aren't immediate -- it will get processed next time Evolution retrieves your mail.

---

### Post by jhenager on 2006-11-16
> **aridus said:**
> I don't remember where it is exactly, but it is something you can set in the preferences. The option is labeled something like 'Save replies with original message' or 'Save replies in same folder as original message'.

Found it in Outlook.
Tools>Options>Preferences>E-mail Options>Advanced E-mail options
"In folders other than the Inbox, save replies with original message"

Didn't know that functionality was there. You might want to suggest this as a product enhancement for Evolution.
I am at work so I can't fish around in Evo for an equivalent right now. Good luck.

---

### Post by aridus on 2006-11-16
> **jimcooncat said:**
> I have an older Evolution from Breezy, so YMMV.

[INDENT]From the menu, "Edit -> Preferences"

Click tab on left, "Mail Accounts"

In the accounts list, select the account that has "[Default]" in it.

Click the "Edit" button. 

Click the "Defaults" tab at the top of the dialog box.

Click the "Always blind-carbon-copy (bcc) to" checkbox so that it's checked.

Fill in your own email address.[/INDENT]

What this does is to send you a copy of every email you send out. You can then apply a rule to it, where Recipients contains *your-friend@somewhere.com*. That way, all your replies to a particular correspondant get a copy automatically filed. 

Not exactly what you wanted, and you have to make a new rule for every contingency you want handled. But this would work if you have a limited number of cases.

Also, because you're actually sending out a copy, the results aren't immediate -- it will get processed next time Evolution retrieves your mail.

Many thanks, I will try this as a stop-gap.

---

### Post by aridus on 2006-11-16
> **jhenager said:**
> Found it in Outlook.
Tools>Options>Preferences>E-mail Options>Advanced E-mail options
"In folders other than the Inbox, save replies with original message"

Didn't know that functionality was there. You might want to suggest this as a product enhancement for Evolution.
I am at work so I can't fish around in Evo for an equivalent right now. Good luck.

Thank you - I will find out how to suggest this as a product enhancement for Evolution.

---

### Post by aridus on 2006-11-17
I have now entered a feature request for this on Bugzilla. It is:

Bug 376303 – In folders other than the Inbox, save replies with original message

---

### Post by AlanRogers on 2006-12-19
> **aridus said:**
> Bug 376303 – In folders other than the Inbox, save replies with original messageBump, I can't find a Bugzilla for Ubuntu or Evolution and that bug number doesn't appear to be valid at [LaunchPad]("http://www.launchpad.net"). Can someone lead a fool by the nose, so I can watch the progress (or not)?

---

### Post by aridus on 2006-12-19
You need to go to bugzilla.gnome.org, and you can find the bug report at

[http://bugzilla.gnome.org/show_bug.cgi?id=376303](http://bugzilla.gnome.org/show_bug.cgi?id=376303)

---

### Post by AlanRogers on 2006-12-19
Thanks, I'll keep an eye because I too am very interested in this feature.

---

