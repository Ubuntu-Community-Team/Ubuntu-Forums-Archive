---
title: "amule not connected"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-08-31
hey guys,

i just installed amule and i can't get it to connect. the default server it has provided wouldn't connect. i tried a several other ones and still, it won't work

is this a known problem for amule? is there a special list of servers?

please tell if you have any idea how to solve this.
any help much appreciated. thanks in advance!

---

### Post by [Alsharifi] on 2007-08-31
yea i just installed amule and i cant get it to connect

it says Kad=off? 

any thing i missed?

---

### Post by shadowboxer_k on 2007-09-01
*bump* :(

---

### Post by shadowboxer_k on 2007-09-01
when i try to download the list of servers in order to choose another one (maybe that's the problem), the whole program crashes. :(

---

### Post by por100pre1 on 2007-09-01
> **shadowboxer_k said:**
> when i try to download the list of servers in order to choose another one (maybe that's the problem), the whole program crashes. :(

Something seems to be wrong that server.met link. Use this one instead: [http://ed2k.2x4u.de/822iu9hc/min/server.met](http://ed2k.2x4u.de/822iu9hc/min/server.met)

---

### Post by shadowboxer_k on 2007-09-01
i'm wondering if i'm doing this correctly...

i just replace the met link that's in the server window with the new one and click connect, but nothing really happens.

here's a screenshot. :/

---

### Post by shadowboxer_k on 2007-09-01
right after posting this i realized my stupid mistake. i got the server list, but now i can't seem to connect to any of them. 
the globe in the lower right corner has two arrows - one yellow and one red. that probably means that i am firewalled. does anyone have any idea how to remove the firewall?

---

### Post by por100pre1 on 2007-09-01
> **shadowboxer_k said:**
> i'm wondering if i'm doing this correctly...

i just replace the met link that's in the server window with the new one and click connect, but nothing really happens.

here's a screenshot. :/

Weird. Close aMule.

Use these commands, and then restart aMule.

```
cd .aMule
```

```
wget http://ed2k.2x4u.de/822iu9hc/min/server.met
```

---

### Post by shadowboxer_k on 2007-09-01
thank you!

now the server list does load but when i select a server from that list, it doesn't want to connect to it.

basically, the following thing happens: i right click the selected server, choose 'connect to server' and in the lower left corner it keeps saying connection lost, whereas the globe in the lower right corner has one yellow arrow and one red one, meaning i'm firewalled and not connected to kad.

this happens to any server from the list i select. i guess i should remove the firewall but i haven't the slightest idea how to do it.

---

### Post by por100pre1 on 2007-09-01
> **shadowboxer_k said:**
> right after posting this i realized my stupid mistake. i got the server list, but now i can't seem to connect to any of them. 
the globe in the lower right corner has two arrows - one yellow and one red. that probably means that i am firewalled. does anyone have any idea how to remove the firewall?

Are you using a router? If so open these ports in the router:

TCP 4662
TCP 4665
UDP 4672

If that doesn't work install Firestarter and do the same in Firestarter:

```
sudo apt-get install firestarter
```

Here's how to use[ Firestarter]("http://www.fs-security.com/docs/policy-page.php").

---

### Post by shadowboxer_k on 2007-09-01
i don't use a router, i'm connected to the local lan network in my area. 

i don't know the first thing about opening ports with ubuntu. i did follow your advice and installed firestarter, however, it doesn't let me use it. it says i need to have root privileges in order to use firestarter. how do i log in as root?

i'm sorry if i'm getting annoying but i really have no idea how to solve this.
thank you for the patience.

---

### Post by Hallvor on 2007-09-01
Hi, there are a few perhaps useful lines in the Howto in my signature. Hope it helps.

---

