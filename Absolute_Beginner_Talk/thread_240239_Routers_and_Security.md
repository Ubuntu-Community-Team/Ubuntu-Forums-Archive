---
title: "Routers and Security"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-08-20
so i've heard that having a router behind your PC is a lot safer than having no router.  i know that ubuntu doesn't open any ports by default, so ubuntu is fine.  


so my question is, if you have windows, just the fact that you have a router makes it safer?  or do you have to manually close ports and such?

also, the very fact that ubuntu closes all ports by default befuddles me.  then how could you surf the web or fetch updates in ubuntu? (which we can from the beginning of a fresh install)

---

### Post by Soarer on 2006-08-20
> **erik1397 said:**
> so i've heard that having a router behind your PC is a lot safer than having no router.  i know that ubuntu doesn't open any ports by default, so ubuntu is fine.  

so my question is, if you have windows, just the fact that you have a router makes it safer?  or do you have to manually close ports and such?

also, the very fact that ubuntu closes all ports by default befuddles me.  then how could you surf the web or fetch updates in ubuntu? (which we can from the beginning of a fresh install)

A router is always a good idea between you and the Internet IMHO. It should hide your internal IP address as a minimum so you can't be contacted from outside to inside. Depending on the router set-up, especially if its Windows plug'n'play (which is a no-no as it is a security risk on its own) you might need to open and/or close some ports.

You can fetch updates & surf because that is a connection initiated from your PC. The data coming back from the Internet is a reply - the people you want to block are not replying to a request from you, they are attempting to break in from outside. Thus Ubuntu allows replies to requests from you through its firewall.

---

### Post by user1397 on 2006-08-20
> **Soarer said:**
> A router is always a good idea between you and the Internet IMHO. It should hide your internal IP address as a minimum so you can't be contacted from outside to inside. Depending on the router set-up, especially if its Windows plug'n'play (which is a no-no as it is a security risk on its own) you might need to open and/or close some ports.okay, so in my situation, i have a typical linksys wireless-B router, from like 2004.  it is conected to my windows/ubuntu desktop via ethernet, and the rest of my windows computers connect to it via wireless.  i never manually closed/opened ports manually from my router's setup page.  

so, basically i plugged it in, installed its software, and let it be.  Is it hiding my internal IP address, and do i need to open/close ports? (which i don't even know how to!)

[quote=Soarer]You can fetch updates & surf because that is a connection initiated from your PC. The data coming back from the Internet is a reply - the people you want to block are not replying to a request from you, they are attempting to break in from outside. Thus Ubuntu allows replies to requests from you through its firewall.[/quote]ah, now it makes sense

---

### Post by oliverb on 2006-08-20
IMO some kind of router is almost essential for a home LAN if you want to share internet access. I would also advise using one on a single PC setup but  that's not such a clear cut decision.

From a security point of view a reasonably configured router provides a firewall between your PC and the internet. I say reasonably configured as some older models didn't protect themselves unless reconfigured so a hacker could reconfigure the router to bypass it. That threat has all but disappeared with current models.

As far as I know the Windows UPnP service has been patched reasonably by now. I think the small security risk is offset by the convenience. The alternative of setting forwarding manually is a nuisance and difficult to explain as the controls differ so much between manufacturers.

---

### Post by Soarer on 2006-08-20
If you go to 'Shield's Up' ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) it will do a scan of your connection and report any open ports and other issues. Sometimes, of course, you need open ports but if you are concerned, you can always close them & see if anything stops working :)

I just did mine & confirmed that Ubuntu Dapper leaves NO ports open.

---

### Post by scxtt on 2006-08-20
a router is 'in front of' your PC, not behind it ...

and a router is like a traffic controller, data makes a request for a port - and if the "traffic controller" allows it, it will forward it to the internal IP specified on your router ... so if you don't forward a port, the data goes no where ...

ubuntu does not block all ports by default if you're not behind a router ... you'll need a firewall for that, and once installed if you don't allow connections - nothing will get through ...

so:
[indent]ubuntu --> modem, no firewall = BAD!
ubuntu + router = good
ubuntu + router + firewall = best[/indent]

---

### Post by stormblue on 2006-08-20
What good is a firewall and a router together?  If you are running a router, you already have a firewall running on the router.

---

### Post by scxtt on 2006-08-20
you can allow traffic through the router, but stop it at your PC (at any time you want) ... so if i want to allow port 80 through my router, but don't feel like allowing it through my box's firewall - i can {instead of logging onto my router and un-enabling port forwarding for port 80} ...

it's not the most useful thing in the world, but ... ;)

---

