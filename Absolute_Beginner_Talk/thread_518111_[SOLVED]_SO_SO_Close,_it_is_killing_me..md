---
title: "[SOLVED] SO SO Close, it is killing me."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by kennyn on 2007-08-05
If I go to [http://www.kennynproductions.com](http://www.kennynproductions.com) within my network, it pulls up fine. But anyone else i ask to test it outside of my local home network, cannot see it. I have my router port forwaded to port 80.

I am pretty sure that my ISP blocks port 80 from the outside. 

I tryed changing the port forwarding to 443 and then nothing pulls up even in my local network.

I am so close I can taste it. Can anyone else please help me. I have a netgear router. Dont know where else to go from here.

---

### Post by Tomosaur on 2007-08-05
> **kennyn said:**
> If I go to [http://www.kennynproductions.com](http://www.kennynproductions.com) within my network, it pulls up fine. But anyone else i ask to test it outside of my local home network, cannot see it. I have my router port forwaded to port 80.

I am pretty sure that my ISP blocks port 80 from the outside. 

I tryed changing the port forwarding to 443 and then nothing pulls up even in my local network.

I am so close I can taste it. Can anyone else please help me. I have a netgear router. Dont know where else to go from here.

```

sudo apt-get install firestarter

```

Try setting a new firewall policy to allow incoming traffic on port 80. Your router may be doing the job just fine, but your machine is actually blocking.

---

### Post by Midahed on 2007-08-05
I'd use a site like ShieldsUp to probe my network and tell me what ports are open, closed or stealth'd.  That might give you a clue as to what's going on.

Mike

---

### Post by Frak on 2007-08-05
Also, make sure your not doing this over WiFi, I don't think its possible to do.

---

### Post by MrFSL on 2007-08-05
This is ABSOLUTELY POSSIBLE over wifi!

---

### Post by Frak on 2007-08-05
> **MrFSL said:**
> This is ABSOLUTELY POSSIBLE over wifi!
OK, now I know.
I now this isn't the LAMP that came with Ubuntu, but have you tried [XAMPP]("http://www.apachefriends.org/en/xampp.html"), IMHO, its much easier to use.

---

### Post by Warren Watts on 2007-08-05
well, I can ping kennyproductions.com and I get a response.

I can telnet to [www.kennyproductions.com](www.kennyproductions.com) on port 25 and I get a login prompt

I can ftp to [www.kennyproductions.com](www.kennyproductions.com) and I get a login prompt

Firefox gives me an error saying the server is taking too long to respond

but Lynx opens the page just fine.....

heres what I get when I follow the "about" link:
> 
About

   This is an example of a WordPress page, you could edit this to put information about yourself or your site so readers know where you are coming
   from. You can create as many pages like this one or sub-pages as you like and manage all of your content inside of WordPress.

     * Categories
          + Uncategorized (2)
     * Archives
          + June 2007
     * Meta
          + Login
          + Valid XHTML
          + XFN
          + WordPress
     * Type and Press Enter

   Day Dream by Jim Whimpey. WordPress runs this show.


Oh wait.....  Now it's working in Firefox!

You must have fixed something...

---

### Post by Midahed on 2007-08-05
Works for me too.

---

### Post by Frak on 2007-08-05
Yay, it works! Maybe a delayed reaction or something. :confused:

---

### Post by MrFSL on 2007-08-05
When updating you dns records it often takes a few days to propagate across the Internet.

---

### Post by Sbarton on 2007-08-05
The OP posts( kennynproductions) the other posts are (kennyproductions) note the missing 'n'
Could this be why.
regards

---

### Post by Midahed on 2007-08-06
> The OP posts( kennynproductions) the other posts are (kennyproductions) note the missing 'n'
Could this be why.
...And as the OP's username here is kennyn, I think you may have a very good point.  He's probably wondering why the site is apparently working for everyone else, but not for him. :)

Mike

---

### Post by kennyn on 2007-08-06
Ok first off, I am totaly a newbie when it comes to this server stuff. SO iam learning ast I go. I am not sure what OP posts mean first off.

Also, I checked my site via IE and Firefox outside of my network and it does not work. Is there anything I can check or anything simple that I am over looking, Can someone please help??

---

### Post by kennyn on 2007-08-06
I think I may have an Idea why the page is pulling up for some people and not for others. If you are going here 

[http://kennyproductions.com/](http://kennyproductions.com/)

and Getting a Blue Website. 

THAT IS NOT MY SITE.

my site is at 

[http://www.kennynproductions.com](http://www.kennynproductions.com)


Now i have tryed many different browsers and so on, any help would be great. Thanks.

---

### Post by OldTimeTech on 2007-08-06
I get a kenny productions on [http://kennyproductions.com...........I](http://kennyproductions.com...........I) get nothing at all at [http://www.kennynproductions.com](http://www.kennynproductions.com).

maybe you forgot the "n" when setting up???

---

### Post by geralddean on 2007-08-06
Works in FF and IE for me.

Got your wordpress blog.

---

### Post by Warren Watts on 2007-08-06
> **kennyn said:**
> If you are going here [http://kennyproductions.com/](http://kennyproductions.com/) and Getting a Blue Website. 

**THAT IS NOT MY SITE.**

my site is at [http://www.kennynproductions.com](http://www.kennynproductions.com)

I think he is saying his site is **NOT [http://kennyproductions.com/](http://kennyproductions.com/)**

His site is **WITH** an "n"

---

### Post by p_quarles on 2007-08-06
As the original poster just noted, the WordPress blog is *not *his site. 

I wonder if this is a DNS problem. Try this: get your numeric IP address and then test that from outside your network. If you still get nothing, that will at least rule out one possibility.

---

### Post by Warren Watts on 2007-08-06
I tried a simple ping to [www.kennynproductions.com](www.kennynproductions.com) and got no response.

I did a traceroute and progress stopped at a router in Atalanta belonging to Cox Communications.
> traceroute to [www.kennynproductions.com](www.kennynproductions.com) (24.252.65.214), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  0.479 ms  0.558 ms  0.376 ms
 2  ppp-69-223-159-254.dsl.wotnoh.ameritech.net (69.223.159.254)  7.428 ms  9.468 ms  7.558 ms
 3  dist2-vlan50.wotnoh.sbcglobal.net (67.36.13.227)  7.633 ms  8.166 ms  7.802 ms
 4  bb2-g8-2.wotnoh.sbcglobal.net (151.164.92.20)  6.414 ms  9.146 ms  7.317 ms
 5  151.164.93.49 (151.164.93.49)  25.861 ms  23.986 ms  26.736 ms
 6  chgobbrj01pos010102.r2.ch.cox.net (68.105.30.205)  24.090 ms  25.202 ms  27.100 ms
 7  elmwdsrj02-so010.rd.no.cox.net (68.1.0.73)  56.908 ms elmwdsrj01-so000.rd.no.cox.net (68.1.0.65)  57.806 ms elmwdsrj02-so010.rd.no.cox.net (68.1.0.73)  56.125 ms
 8  68.11.14.6 (68.11.14.6)  56.945 ms 68.11.14.30 (68.11.14.30)  56.880 ms 68.11.14.6 (68.11.14.6)  56.885 ms
 9  stchcmtk01-gig0100.no.no.cox.net (68.11.13.134)  57.564 ms stchcmtk01-gig0200.no.no.cox.net (68.11.13.138)  57.896 ms  56.747 ms
10  * * *

whois 68.11.13.134
Cox Communications Inc. COX-ATLANTA (NET-68-0-0-0-1) 
                                  68.0.0.0 - 68.15.255.255
Cox Communications NETBLK-NO-RDC-68-11-0-0 (NET-68-11-0-0-1) 
                                  68.11.0.0 - 68.11.127.255

# ARIN WHOIS database, last updated 2007-08-05 19:10


If I query whois for the IP that DNS provides for kennynproductions.com, I get:
>  whois 24.252.65.214
Cox Communications Inc. NETBLK-COX-ATLANTA-8 (NET-24-248-0-0-1) 
                                  24.248.0.0 - 24.255.255.255
Cox Communications NETBLK-NO-RDC-24-252-64-0 (NET-24-252-64-0-1) 
                                  24.252.64.0 - 24.252.127.255

# ARIN WHOIS database, last updated 2007-08-05 19:10
but if I query whois for kennynproductions.com, I get:
> whois kennynproductions.com

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to [http://www.internic.net](http://www.internic.net)
for detailed information.


   Domain Name: KENNYNPRODUCTIONS.COM
   Registrar: GODADDY.COM, INC.
   Whois Server: whois.godaddy.com
   Referral URL: [http://registrar.godaddy.com](http://registrar.godaddy.com)
   Name Server: NS18.ZONEEDIT.COM
   Name Server: NS3.ZONEEDIT.COM
   Status: clientDeleteProhibited
   Status: clientRenewProhibited
   Status: clientTransferProhibited
   Status: clientUpdateProhibited
   Updated Date: 01-aug-2007
   Creation Date: 01-aug-2007
   Expiration Date: 01-aug-2008

>>> Last update of whois database: Mon, 06 Aug 2007 16:11:40 UTC <<<

Registrant:
   [www.kennyn.com](www.kennyn.com)
   136 Murray Hill Drive
   Destrehan, Louisiana 70047
   United States

   Registered through: GoDaddy.com, Inc. ([http://www.godaddy.com](http://www.godaddy.com))
   Domain Name: KENNYNPRODUCTIONS.COM
      Created on: 01-Aug-07
      Expires on: 01-Aug-08
      Last Updated on: 01-Aug-07

   Administrative Contact:
      Naquin, Kenneth  [email]kenny@kennyn.com[/email]
      [www.kennyn.com](www.kennyn.com)
      136 Murray Hill Drive
      Destrehan, Louisiana 70047
      United States
      (504) 232-1072      Fax -- 

   Technical Contact:
      Naquin, Kenneth  [email]kenny@kennyn.com[/email]
      [www.kennyn.com](www.kennyn.com)
      136 Murray Hill Drive
      Destrehan, Louisiana 70047
      United States
      (504) 232-1072      Fax -- 

   Domain servers in listed order:
      NS3.ZONEEDIT.COM
      NS18.ZONEEDIT.COM


Now I noticed that they listed kennyn.com in the address of the registrant.

I tried browsing to [www.kennyn.com](www.kennyn.com) and it worked...here is what I got:
[IMG]http://kingbeetle.servehttp.com/images/kennyn.png[/IMG]

I notice the phone number listed is the same as the regististrant for [www.kennypoductions.com](www.kennypoductions.com), so I can only assume that's you...

---

### Post by Midahed on 2007-08-06
> **kennyn said:**
> Ok first off, I am totaly a newbie when it comes to this server stuff. SO iam learning ast I go. I am not sure what OP posts mean first off.

Also, I checked my site via IE and Firefox outside of my network and it does not work. Is there anything I can check or anything simple that I am over looking, Can someone please help??
'OP' mean 'original poster', i.e. kennyn in this case.

Did you try one of the 'security check' sites like ShieldsUp at [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)  to see if you have the requisite ports accessible from the outside world?  If you go to that site and click the Shields Up logo, scroll about half way down the page and click Shields Up again.  It will tell you your 'machine name' and give you a load of text to read.  Click 'proceed' and then click the 'all service ports' button.  After a few minutes the site will report which ports are open.

Is your PC  directly connected to the internet via a cable or DSL modem, or do you connect via a router?

**[EDIT]**  ...and while I was typing someone else has made a load of progress on the investigation.  Don't ya hate it when that happens ;)

kennyn.com resolves to 68.178.254.22 whereas kennynproductions.com resolves to 24.252.65.214

Mike

---

### Post by kennyn on 2007-08-08
Ok, let just say I am there but just frustrated. I finally got my server to work. The downfall is my ISP blocks port 80, so I had to set my port to 81.

So if you go to: [http://www.kennynproductions.com:81](http://www.kennynproductions.com:81) you should get my website.

This is really agrivating, I dont want to have to put in :81 after it. Does anyone know how to disguise this or fix this without having to get a new domain and mask it to that address??

Thanks.

Also one more question, my current full time job blocks anything on 80, 81 etc. I know that they do not block 443. Any way of getting around this so that i can pull my website up here from work as well as everyone else in the real world still being able to see it??

---

### Post by Frak on 2007-08-08
You may want to forward your domain to your IP : Port, i.e. kennynproductions.com fowards to 24.252.65.214:81
Hope that helps.

---

