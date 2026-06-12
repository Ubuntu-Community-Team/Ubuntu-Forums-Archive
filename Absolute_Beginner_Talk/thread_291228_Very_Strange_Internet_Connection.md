---
title: "Very Strange Internet Connection"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by bddubai on 2006-11-02
Thanks for taking the time to read this.

  I cannot get my Internet set up properly. 

  [B]Here's a description of the problem: 
[/B]
  I can view Web pages when entering numbers (e.g. [http://198.133.219.25/index.html)](http://198.133.219.25/index.html)). This is for Cisco Systems. It is slow, but it works; however, when I try the same for the standard Web address ([http://www.cisco.com/)](http://www.cisco.com/)), the site/page doesn't load.

  In the *Network Tools*, I can ping both addresses listed above. Both ping just fine. I have phoned my Internet Service Provider (ISP). After several attempts at changing configurations with both *Network Settings* and *Connection Settings* in Firefox, we had no luck. He stated that he was unable to assist any further.

  [B]Here's what I have:
[/B]
  I am using an ADSL router (Creative Broadband Blaster 8015U) with an Ethernet connection going into the computer. Our ISP uses PPPoA. Presently, in the *Network Settings*, I have the *Automatic Configuration (DHCP)* selected; I have tried a manual configuration with my ISP -- no difference. *The Enable this connection* box is "ticked." I have inputed a DNS Server setting; it's still there, without it the ping wouldn't work.

  With Firefox, I have the *Direct Connection to Internet* selected, and, like before, have tried the two other selections (even the Manual Proxy!) and had the same result: I can type numbered addresses, but not standard addresses.

  If I take the lead out of the Ubuntu machine, and put it in my notebook running Windows, it works just fine. Therefore, I know it's configured correctly for my ISP.

  I think that's about everything I can tell you.

  This is my first attempt at Linux. I have read a "blood-shot" eyeball amount of threads and have no clue to all the coding that I see. I hope there's a simple solution. If not, with your patience, I'm up for the challenge.

  Thank you again.

---

### Post by mahy on 2006-11-02
hmmm, you're saying it works in windows and works for pinging. How about trying other browsers as well? The choice is yours: Opera, Konqueror, Elinks ...

---

### Post by Paul41 on 2006-11-02
Have you tried to disable IPv6? I don't know if that is going to help, but you could at least try.

Type about:config in the address bar in Firefox, filter for IPv6, then disable it.

---

### Post by caravel on 2006-11-02
This points to it being a DNS related problem.  IP addresses work, domain names do not.  You need to either point to your router's IP as the DNS server or enter your primary and secondary DNS server addresses manually, as DHCP is obviously not doing it automatically.

---

### Post by Carlos Santiago on 2006-11-02
As Caravel said, it is a DNS problem. 
If it works on windows, on a DOS console type 'ipconfig /all', then write down the DNS servers address.
On Linux, in the network control panel, write the previous DNS server addresses.

---

### Post by bddubai on 2006-11-02
[I]As Caravel said, it is a DNS problem.
If it works on windows, on a DOS console type 'ipconfig /all', then write down the DNS servers address.
On Linux, in the network control panel, write the previous DNS server addresses.[/I]

  Thanks for the feedback.

  Regarding the above reference, however. I got you - I think! Go to the **Start > Run** in Windows, yeah? From there what would I type exactly?

  If I'm following correctly, I would then obtain the DNS server addresses. After, I need to go back to Ubuntu and type these into the *Network Settings*.

  Is this correct?

  Thanks again!

---

### Post by pattymnaish on 2006-11-02
In the run box, type "cmd". Then enter the "ipconfig /all" command in the DOS console that appears.

---

### Post by Carlos Santiago on 2006-11-03
As pattymnaish said, type "cmd" on the run box, then type "ipconfig /all"

Yes, you obtain the DNS server addresses from Windows. After, you go back to Ubuntu and type these into the Network Settings.

---

