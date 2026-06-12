---
title: "Evolution freezes at password"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by sanicki on 2007-03-23
I am running Evolution on Edgy against MS Exchange.

When initially configuring the account I learned that unless I set a password for my keyring prior to setting up Evolution it would request my Exchange password the next time I ran Evolution and freeze up before I could enter it.

If I had my keyring password set it would remember my password and not prompt me for it again and therefore not freeze.

Worked like a charm for a few days of testing.

However I'm still trying to get access to my GAL so I was playing with the GAL URL. Next login up comes the password prompt and it freezes. So in lieu of a workaround I need a solution for Ubuntu to be viable for our office OS.

Can anyone help?

---

### Post by johnnymac on 2007-03-23
Hmm...if it's freezing on the password, that means that the exchange backend is having trouble talking to the MS Exchange Server on the URI you passed it.  So for example....I use Evolution for my work email (and yes we have  a poopy MS Exchange Server).  So - I have to explicitly call out "exchange" as follows.

[https://mymail.mycompany.com/exchange](https://mymail.mycompany.com/exchange)

If I do not specify the exchange path I get frozen on password authentication.  If this is still not working....MS Exchange does have a web interface.

---

### Post by sanicki on 2007-03-23
I use the same ([https://mymail.mycompany.com/exchange)](https://mymail.mycompany.com/exchange)).

But it's not so much a freeze-upon-pw-submit as pw-prompt-freezes. I can usually get a character or two in, but then it locks up before I can submit.

(like [http://gnomesupport.org/forums/viewtopic.php?t=12281](http://gnomesupport.org/forums/viewtopic.php?t=12281))

---

### Post by sanicki on 2007-03-26
Workaround discovered!

Start Evolution in offline mode ('evolution --offline'). Enter pw and connect. You may connect normally thereafter.

---

### Post by ariel on 2007-06-01
My workaround was to use:

evolution --disable-eplugin

---

### Post by kklingerman on 2007-09-05
> **ariel said:**
> My workaround was to use:

evolution --disable-eplugin

Has anyone figured out which e-plugin is causing this crash?  I also have it and the work around fixes it.

---

### Post by sanicki on 2007-09-12
Sorry, I didn't find any answers. I ended up punting on Ubuntu in favor of Kubuntu with the hope that the Kontact Exchange plugin would be more successful. It was okay, but ultimately the best solution for us was to ditch Exchange in favor of Zimbra and use their robust webmail client.

---

### Post by RikBlankestijn on 2007-09-22
> **sanicki said:**
> Workaround discovered!

Start Evolution in offline mode ('evolution --offline'). Enter pw and connect. You may connect normally thereafter.

Finally! ;) Thanks.

---

