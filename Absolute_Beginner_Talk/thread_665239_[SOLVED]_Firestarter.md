---
title: "[SOLVED] Firestarter"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2008-01-12
There is a lot of blocked connections showing up in the events tab:
[http://s74.photobucket.com/albums/i244/BlastinOnYall/?action=view&current=Screenshot-6.png](http://s74.photobucket.com/albums/i244/BlastinOnYall/?action=view&current=Screenshot-6.png)

Should I be worried?

Also, firestarter fails to start when my computer boots up. I read that this is because it's trying to start before my internet connection. It starts up fine when I do it manually. Any fixes for this?

---

### Post by Herman on 2008-01-12
You must be connected directly to the internet somehow are you? What kind of internet connection do you have?

I used to get a lot of traffic like that when I was on dial-up, but now that I have broadband, there's a Linux kernel in my broadband modem that keeps all that out.

If you don't have any services installed, you shouldn't have any open ports in Ubuntu so you shouldn't even need a firewall, so therefore I don't think you need to be worried.

I don't know why they send out all those random siignals over the internet, I wonder if they are hoping to find an unsecured machine they can hack into. I read an unprotected Windows computer would only last about fifteen minutes without being compromised, I'm not sure if it's true or not.

Just for something to do you can go 'System'-->'Administration'-->'Network Tools', and select the Whois tab.
Type some of those IP numbers into the Domain Address field there and click the Whois button.
Some of yours are from shaw communications in Calgary, but some are from Korea, and that's all they say. One was from China. It's just interesting, I don't know if it matters. It's something to do if you're bored.

I don't think you need to worry.

Are you sure Firestarter doesn't start when your system starts? I think it would be running, but you just aren't aware of it maybe.

If you want to run a check on your system's security, get another Ubuntu computer and hook them both up to the same network.
Then you can go 'System'-->'Administration'-->'Network Tools', and select the Port Scan tab and enter the IP address of the other Ubuntu computer.
Neither Ubuntu computer should show any open ports, so it should scan for a long time and nothing will happen. It there are open ports, it will find them within a minute or so. Uninstall services that have opened ports in your computer. You can always install them again some day when you need them.

I have a test computer I installed a few services in on purpose, to open a few ports. I'm playing with networking stuuf just for fun. It has Firestarter in it and I reboted mine to see if Firestarter still work after a reboot and a port scan indicates that Firestarter is working for sure in mine at least, right from boot-up.
If you have another Ubuntu box you should be bale to verify that too.

Regards, Herman :)

---

### Post by fiddledd on 2008-01-12
just to add that AFAIK Firestarter is only a GUI configuration tool for IPTables. It doesn't need to run unless you want to alter rules etc.

---

### Post by OrangeCrate on 2008-01-12
You can also check if your firewall is working by testing it here:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

The default Firestarter set-up will show all ports stealthed.

This should answer your other questions:

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by piratesmack on 2008-01-12
Thanks, that's good to know

i know firestarter wasn't starting because when I boot in verbose mode, there is a line that says something like:
> Starting firestarter firewall...........[COLOR="Red"]FAILED[/COLOR]

But I decided to switch to the lokkit firewall and I'm having no problems with it

---

