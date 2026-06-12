---
title: "Using gnome network manager in kubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2008-01-10
Hey everyone, 

I would like to use the GNOME network manager in my latest install of Kubuntu 7.10. This manager seems to work much better with encrypted wireless signals. What packages should I install and uninstall?

---

### Post by Sef on 2008-01-10
Applications > Add/Remove > search > gnome network manager.

Or

System > Administration > Synaptic Package Manager > search > gnome network manager

Add/Remove will let you know if you have to use synaptic.  The depedencies will be taken care of automatically.

---

### Post by AngryMallard on 2008-01-10
I went to Add/Remove Programs and searched for "gnome network manager" and nothing came up. So I went to Internet and installed "Network Manager." Its package name was "network-manager-gnome."

After the install finished, I restarted my computer but nothing has changed. There is not an icon for it anywhere and when I alt+F2 and try to execute "network-manager-gnome" it cannot find the command.

What did I miss?

---

### Post by mrjerryk on 2008-01-14
I would like to know how to add this add well.  I accidentaly removed it from my panel yesterday and now I cannot connect to my wireless router.

---

### Post by MadEgg on 2008-01-18
I found out that the actual command for starting network-manager-gnome is nm-applet

It works for me to connect to the network at my university using WPA/TLS encryption, while knetworkmanager does not. Can anyone explain this?

KNetworkmanager has the same settings so it should also work I would say, but apparently is doesn't.

---

