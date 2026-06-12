---
title: "amule settings"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by osiris.osiris on 2007-06-25
I don't now what I must do with my amule configuration. I have tried to configure it, but my amule doesn't works.
However, with Windows (emule) I download whatever I want.
Though I am novel and Windows is easier for me, I wish use Ubuntu, but I need amule. 

Can anyone help me? Thanks in advance

My settings: download 250kB/s; upload 10kB/s; TCP 8888; UDP 8889

---

### Post by sad_iq on 2007-06-25
What doesn't work with amule?? Connecting(can you connect to a server???If not post your errors)??? Downloading??? Is it configured? Have you opened your ports in your router?? Do you have static ip ?? Please be more specific about your problem...and well figure it out!!!

---

### Post by RomeReactor on 2007-06-25
Hi. Have you tried opening ports 8888 (TCP) and 8889 (UDP) in both Ubuntu (through Firestarter) and your modem/router? I also suggest you take a look at [this list of ports numbers]("http://www.iana.org/assignments/port-numbers") and what do they stand for, as it is recommended you specify an unassigned port to aMule and/or BitTorrent. If you don't have Firestarter installed (I recommend it to manage your firewall), you can do so through Synaptic (**System-->Administration-->Synaptic Package Manager** (just search for **Firestarter**) or through the terminal (**Applications-->Accessories-->Terminal** by typing the following (or copy/paste):
```
sudo apt-get install firestarter
```
You can find Firesterter (once it's installed) in **System-->Administration-->Firestarter**.

---

### Post by Hallvor on 2007-06-25
> **osiris.osiris said:**
>  My settings: download 250kB/s; upload 10kB/s; TCP 8888; UDP 8889

Why don`t you set your upload a little higher? Whatever you download is uploaded by someone else, so be generous.

---

