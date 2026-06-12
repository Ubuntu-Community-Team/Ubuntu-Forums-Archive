---
title: "Fn Keys on LG R500"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by delphin on 2008-04-18
Hi,
i have researched a lot on the net including a wonderful lesson on Fn keys recognition.
The replies have been  that the procedure won't work for my laptop .
I have an LG R500 laptop which in the short time i have linux ( about 6 weeks) works fine and am getting more accustomed to it daily. I would like the Fn keys to be usable. If anyone has any experience or advice it would be deeply appreciated.
thanks
heinz

---

### Post by Brucevdk on 2008-04-20
Check out the following resources (also  see *man acpid*:
[LIST]
[*] [Ubuntu Wiki: LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch)
[*] [ThinkWiki: How to get special keys to work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)
[*] [Fedora Wiki: Key Processing](http://fedoraproject.org/wiki/SIGs/Laptop/HotKeys/KeyProcessing)
[/LIST]

Those should give you all the information you'll need. I'll use this post to give you some pointers from the top of my head, but make sure you read the above linked resources (especially the one from the ThinkWiki).

First of all you can use *tail -f /var/log/acpid* to keep track of the events that are generated, for example the Fn + F9 combination on my IBM ThinkPad R51 generates the following event:
```

[Sun Apr 20 11:37:51 2008] received event "ibm/hotkey HKEY 00000080 00001009"
[Sun Apr 20 11:37:51 2008] notifying client 6650[107:116]
[Sun Apr 20 11:37:51 2008] notifying client 7369[0:0]
[Sun Apr 20 11:37:51 2008] completed event "ibm/hotkey HKEY 00000080 00001009"

```

If we wanted to handle this event we'd simply place a rule in */etc/acpid/events* with the content:
```

# Custom stuff!
event=ibm/hotkey HKEY 00000080 00001009
action=/etc/acpi/customstuff.sh

```

Now all you have to do is edit */etc/acpi/customstuff.sh* to do what you want it to do.

Make sure you restart ACPI Daemon so it loads the new rules using:
```

sudo /etc/init.d/acpid restart

```

---

### Post by delphin on 2008-04-24
Dear Brucevdk
i tried to read up on you but only found your age and that you live in Holland. I admire young people getting into open source Linux and delving into the depths of it.  So with your reply, which i really appreciate so much and thank you for dearly, you gave me lots to work with the subject and of course Linux in general. I'll let you know the result ultimately.
thanks for now
heinz

---

