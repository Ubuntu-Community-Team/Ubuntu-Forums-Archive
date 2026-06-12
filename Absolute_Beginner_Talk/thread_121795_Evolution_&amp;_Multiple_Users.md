---
title: "Evolution &amp; Multiple Users"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by paulgroovy on 2006-01-26
Hi,

I just set up evolution with my gmail account.  And then I added my wifes account aswell.  However, evolution mixed up the two inboxes.  Is there anyway to keep the two separate?  And is there any way to import your whole gmail, sent items, contacts etc.  I can only seem to get the inbox.  I need some help with this.

Thanks.

---

### Post by amohanty on 2006-01-26
Do you and your wife have separate login accounts?

AM

---

### Post by paulgroovy on 2006-01-26
Yes, we have completely separate accounts and I want to keep it that way.  I do not want our accounts to be mixed together, which is what evolution is doing.  I aslo want to sync my palm pilot, but only with my information, and not hers, but how would I do that.  Is there any way the accounts could be kept completely separate?

Oh, and is there any way to import from google, or any other web based mail, all contacts info and all previous sent mails?

---

### Post by paulgroovy on 2006-01-26
I have another question.  How can I import my inbox from evolution into Thunderbird?  I got evolution receiving mail, but could not get it to send.  I got Thunderbird to do both.  So now I want to import my entire inbox from evolution into Thunderbird.  Any ideas?

Thanks

---

### Post by twowheeler on 2006-01-26
[QUOTE=paulgroovy]Yes, we have completely separate accounts and I want to keep it that way.  I do not want our accounts to be mixed together, which is what evolution is doing.  I aslo want to sync my palm pilot, but only with my information, and not hers, but how would I do that.  Is there any way the accounts could be kept completely separate?
[/QUOTE]

Just to be clear, you and your wife login to different desktops with different user names?  I have never heard of evolution mixing together users if they are on separate desktops.  If you are sharing a desktop though I could see how you could have trouble.

---

### Post by paulgroovy on 2006-01-27
OK, my wife and I use the same desktop.  We both log in as the same user.  However, Thunderbird keeps different accounts separate, why not Evolution?  I just want evolution to keep our inbox, outbox etc etc separate like Thunderbird does.

---

### Post by amohanty on 2006-01-27
> However, Thunderbird keeps different accounts separate, why not Evolution? I just want evolution to keep our inbox, outbox etc etc separate like Thunderbird does.

Thats probably because in T'bird you configured two separate pop accts, which are maintained in separate files and folders and for all practical purposes are different _profiles_.

Evolution on the other hand tries to be more Outlook like, as a result it has only one real Inbox, and multiple accts deposit all stuff into it. The easiest solution is to setup a rule to directly drop the email to your wife's email address into a local folder and yours into another.

HTH
AM

---

### Post by persev on 2008-01-30
> **amohanty said:**
> Thats probably because in T'bird you configured two separate pop accts, which are maintained in separate files and folders and for all practical purposes are different _profiles_.

Evolution on the other hand tries to be more Outlook like, as a result it has only one real Inbox, and multiple accts deposit all stuff into it. The easiest solution is to setup a rule to directly drop the email to your wife's email address into a local folder and yours into another.

HTH
AM

And that is why Evo sucks.

---

### Post by stchman on 2008-01-30
If you use different login accounts on the same computer each user will have their own ~/.evolution folder and everything can be maintained separately.

Otherwise you will need to use filters to separate email.

---

### Post by dcstar on 2008-01-30
> **paulgroovy said:**
> OK, my wife and I use the same desktop.  We both log in as the same user.  However, Thunderbird keeps different accounts separate, why not Evolution?  I just want evolution to keep our inbox, outbox etc etc separate like Thunderbird does.

Different packages do different things, if you want Thunderbird features then use that product.

Evolution doesn't do it for POP accounts because it is not designed to do it, and most likely thousands of people wouldn't want it to work that way - myself included.

If you used IMAP accounts they would be kept separate, so why not try that instead of POP?

---

### Post by persev on 2008-05-19
> **dcstar said:**
> Different packages do different things, if you want Thunderbird features then use that product.

Evolution doesn't do it for POP accounts because it is not designed to do it, and most likely thousands of people wouldn't want it to work that way - myself included.

If you used IMAP accounts they would be kept separate, so why not try that instead of POP?

My broadband provider gives me so many free POP accounts, one of which I use for business and one for junk. I was going to be moving and wanted a portable email account that was compatible with linux/thunderbird,etc and chose Gmail. It is easier to not use a feature than to not have the feature at all, so many of us now have a useless program Evolution BUNDLED with the OS, just like Microsoft's crap programs. It's a good thing we have Thunderbird as a choice because we aren't given one under Evo, otherwise I would be stuck using KDE which is so ugly it actually distracts me.

---

### Post by hugmenot on 2008-05-19
Just use IMAP for the Google account.

---

