---
title: "Outlook Web Access in Ubuntu"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by phanboy_iv on 2005-10-19
Is there away to view my student email from within Evolution?
My school uses Microsoft Outlook, and currently the only way to see my mail is to use an Internet browser

---

### Post by KingBahamut on 2005-10-19
You can use Evolution to reference an Outlook Exchange server.

---

### Post by kaplanmyrth on 2005-10-19
I've connected to OWA using Firefox in the past, so you should try that first. Otherwise, if OWA really requires Internet Explorer, you can install Wine and run Internet Explorer.

There's a package [here]("http://www.tatanka.com.br/ies4linux/") that installs wine, IE and Media Player all at once, and it works under Breezy at least.

Good luck,
&y

---

### Post by gpw797 on 2005-10-19
OWA doesn't require IE.. I access OWA all the time through firefox (on ubuntu)

---

### Post by phanboy_iv on 2005-10-25
I know about accessing the Outlook Web interface with Firefox, but what I want 
to know is, can I manage that mail from within Evolution or Thunderbird and how do I set that up..?

---

### Post by dummkhan on 2008-07-07
Hi

This is a pretty old message but anyhow I would answer to this. I think you could access mail from exchange server using evolution-exchange package. Just type 

> sudo apt-get install evolution-exchange

---

