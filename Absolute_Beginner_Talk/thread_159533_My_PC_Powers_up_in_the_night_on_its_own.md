---
title: "My PC Powers up in the night on its own"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Healey on 2006-04-13
Hi

I have noticed recently that after I have powered down my pc before going to bed for the night - It switches itself on again at some point during the night !!

When I look at the pc in the morning I am greeted whith the login screen !!

What causes this ?? I hve noticed it about 4 times now.

I am using Ubuntu 5.10 and my mother board is a Gigabyte GA-7VKMLS

Hope you can help as its a bit strange and also a great waste of power !!

Thanks

Regards

Healey

---

### Post by Thirsteh on 2006-04-13
If your BIOS supports "Power on after power loss", try disabling it. I don't know why, but some motherboards seem to be buggy when it comes that, seem to register a power cut when it's really just minor interference or summat.

Alternatively, does your BIOS have a turn on-timer? If so, is it set to some time in the night?

---

### Post by krusbjorn on 2006-04-13
Perhaps there is something with your wall socket that cuts the electricity and then when it comes back on, the computer powers on? Or perhaps you have unfinished business with some of your ancestors?

---

### Post by Madpilot on 2006-04-13
Next time you log out, make sure you haven't selected the "Restart the Computer" option - that's the only thing I can think of that would cause this sort of behaviour.

(either that, or you sleepwalk and turn the PC on yourself, but don't remember doing it...) ;)

---

### Post by Healey on 2006-04-13
Hi

Thanks for your replies

It has only happened very recently and as far as I know I dont have any power problems, ghosts or practical jokers in the house - lol

So I will look at the bios and see if I can work anything out, my worry is I have not made any recent changes to the bios so why would I need to now !!!!!! - 

Could it be a faulty switch ??

Regards

Healey

---

### Post by meborc on 2006-04-13
[QUOTE=Healey]...It has only happened very recently and as far as I know I dont have any power problems, ghosts or practical jokers in the house...[/QUOTE]
i was just about to ask if zou have any small brothers/sisters :)

hey, i had to reinstall my computer 3 times before i realized that my sister was deleting important files every time she loged out cuz she had read somewhere it was 'good' for the computer...

---

### Post by gnu2tux on 2006-04-13
you have wake on lan enabled in the bios?

Al.

---

### Post by Healey on 2006-04-13
Hi 
Thanks for reply
Yes I have "wake on LAN" enabled in bios because this is the default value and it has been this way for a long time but it has only started happening

Should I disable it ??

Healey

---

### Post by krusbjorn on 2006-04-13
Try disabling it and see if it helps. If it does, but you use the wake-on-LAN-function, it might be an idea to flash a newer/newest version of your BIOS if there is one.

---

### Post by Healey on 2006-04-13
Hi

Ok its easy to try - but why would it suddenly give this trouble ??

It has never happened before and I have never changed it !!!

Strange !!

Healey

---

### Post by gnu2tux on 2006-04-13
yes, disable wake-on-lan.

I always switch it off, it's not very useful unless you have a specific need for it.

Do you have a firewall between you and the net or do you have a direct connection? If you have a direct connection you may be getting port-scanned by people of 'dubious nature' on the net and something is waking it up.

Either way, probably nothing to worry about. 

Al.

---

### Post by Healey on 2006-04-13
Hi
Thanks for reply

Ok i will do that - I dont really know exactly what it is fo,r so I guess I dont need it !

Yes I have two firewalls - Firestarter and a firewall in my "Zoom" router/modem

Thanks and regards

Healey

---

### Post by tribaal on 2006-04-13
Happened to me after I changed my DSL router. My router was sending me WoL packets (they're called "magic packets" sometimes) every hour, by default. I turned it off on my router, so that I can still use the wake on lan features of my BIOS if need be.

You should check your router's config too maybe... typing 192.168.1.1 in the firefox adress bar should let you do that (you'll need that admin password you noted down during installation).

- Trib'

---

### Post by Healey on 2006-04-13
Hi
Thanks for reply

I am a little new at all this, but I have looked at my Zoom setup and cannot see any reference to the Wol packets that you refered too !!

I will see if I still get the problem after disabling Lan wake up

Thanks

Healey

---

