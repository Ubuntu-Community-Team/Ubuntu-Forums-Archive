---
title: "DSL modem problems"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Quinn The Eskimo on 2008-02-17
OK
i've searched the board for answers, but haven't found anything useful so here's my problem...

i had cable internet and had no problems
i just switched to dsl
i went into my modem's firewall settings
there are 5 settings: Custom Security, No Security, Minimum Security, Typical Security and Maximum Security

if i set it to No security or Minimum Security, my torrents are slow and my browser is extremely slow(5 minutes or more to load a page), but i can use pidgin
if i set it to Typical Security, my torrents are a little faster(still slow, but faster), my browsing of the internet is a little bit faster(but also still way too slow) and i can't use pidgin
if i set it to Maximum Security, my torrents won't download at all, i can't use pidgin, but my browsing speed is fast enough to stream video

i don't know enough about anything to even try custom, the edit option on it bring up a page of what might as well be gibberish to me

i use azureus for bit torrents, my ports are forwarded and all my torrents are "green"
does anyone know how i can configure it so i can download torrent and still be able to surf the net and chat with my friends at the same time or am i doomed to only be able to do one thing at a time and constantly have to switch firewall settings?

---

### Post by Quinn The Eskimo on 2008-02-17
bump

---

### Post by oilchangeguy on 2008-02-17
please explain what you are doing to/with the firewall. what firewall are you using? are you using firestarter to change the iptable settings? if so don't! iptables does the job without any un-needed user input.

---

### Post by Quinn The Eskimo on 2008-02-17
> **oilchangeguy said:**
> please explain what you are doing to/with the firewall. what firewall are you using? are you using firestarter to change the iptable settings? if so don't! iptables does the job without any un-needed user input.

it's the modem firewall settings
all i'm doing is choosing the different firewall options in the modem

i have no idea what firestarter or iptable is

---

### Post by oilchangeguy on 2008-02-17
i've not seen a modem with a firewall. are you using a wireless router?

---

### Post by Quinn The Eskimo on 2008-02-17
no router, well i guess the modem is the router, it has wireless as well as 4 pots for ethernet
i have the wireless disabled in the dsl modem since i down have a wireless modem in my pc

---

### Post by Quinn The Eskimo on 2008-02-17
when i go into the modem and click "firewall"
i get this
[IMG]http://i66.photobucket.com/albums/h269/themightyquinn71/Screenshot.png[/IMG]

---

### Post by oilchangeguy on 2008-02-17
the logical choice would be no security. because of ubuntu's built in firewall. but from your first post, that doesn't work either. have you set networking to auto config, and not the default roam? go to system, admin, networking. highlight the ethernet card, properties, uncheck roaming, and select auto. and save your settings.

---

### Post by iansane on 2008-02-17
Yeah there are combo router/modems that have firewalls. Obviously, looking at the pic you posted, if that is plugged directly to your cable line from outside, that's what you have. Looks like they are taking lessons from windows on how to confuse things with built in default settings like that instead of letting you set each thing individually. I think youl'll just have to figure out the custom settings if the built in ones are causing trouble.

---

### Post by Quinn The Eskimo on 2008-02-17
> **oilchangeguy said:**
> the logical choice would be no security. because of ubuntu's built in firewall. but from your first post, that doesn't work either. have you set networking to auto config, and not the default roam? go to system, admin, networking. highlight the ethernet card, properties, uncheck roaming, and select auto. and save your settings.

i just tried that and it doesn't seem to change anything
thank you though
i guess it could just be that downloading torrents (even though the speed isn't very fast) could be slowing down my ability to view web pages

---

