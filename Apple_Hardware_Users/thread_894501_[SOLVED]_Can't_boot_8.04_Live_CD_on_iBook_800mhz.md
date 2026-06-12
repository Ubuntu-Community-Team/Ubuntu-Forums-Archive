---
title: "[SOLVED] Can't boot 8.04 Live CD on iBook 800mhz"
date: 2008-08-19
forum: Apple Hardware Users
---

### Post by the_nite_owl on 2008-08-19
I have an 800Mhz iBook with 40Gig HD and 384MB ram.
The airport card was missing when I received the iBook.

I am trying to boot 8.04 PPC but it always hangs on a blank screen.  I have tried a few of the optional startup parameters but so far no luck.

Any suggestions?

When I receive the iBook it had a 64MB DIMM installed that was not the original.  Originally it came with a 256 + the built in 128.  I put a 256 into it to bring it back to 384MB.

This laptop sat for a long time with no charge.  Does it need some type of reset to update the clock or make it recognize hardware changes?  I am not very familiar with MAC.

I installed OSX 10.4 on it but was not able to get it to connect to the network using a standard DHCP automatic setup and the built in Ethernet port.  I thought I would try Ubuntu Live CD to see if it could connect and verify that the network jack is working.  Might have to buy an airport card for it but have fears if the built in ethernet is not working the airport socket might be out too.  I was told when I got it that the airport card was not working so they removed it.

---

### Post by cyberdork33 on 2008-08-19
> **the_nite_owl said:**
> I am trying to boot 8.04 PPC but it always hangs on a blank screen.  I have tried a few of the optional startup parameters but so far no luck.It is helpful to note what is the last thing you can see (if anything). You might also want to try the alternate installer.

> **the_nite_owl said:**
> This laptop sat for a long time with no charge.  Does it need some type of reset to update the clock or make it recognize hardware changes?  I am not very familiar with MAC. there is a "date bug" on PPC Ubuntu, but I don't know if it affects the latest release.

> **the_nite_owl said:**
> I installed OSX 10.4 on it but was not able to get it to connect to the network using a standard DHCP automatic setup and the built in Ethernet port.  I thought I would try Ubuntu Live CD to see if it could connect and verify that the network jack is working.  Might have to buy an airport card for it but have fears if the built in ethernet is not working the airport socket might be out too.  I was told when I got it that the airport card was not working so they removed it.

It does indeed sound like the port is bad. It should not effect the airport connector though. (Also, the airport was likely removed because they can fetch a better price for it by itself). You can also use other compatible cards that can be a bit cheaper. I used to use a hermes / orinoco card in my G3 iBook.

---

### Post by the_nite_owl on 2008-08-19
Drawing a blank on what the boot app is called but I get it's screen and I select the option that gives me all of the optional boot parameters.
I have tried several of the options. I am at work now and do not have the iBook so I am going by memory.  
The screen changes immediately showing various bits of data then goes blank.  After a minute or two it stops accessing the CD and proceeds no further.

The odd thing with the built in ethernet is that on my router I can see the iBook exists on the network but for some reason it never picks up an IP address.  I may be missing a setting somewhere but it seems pretty straightforward.

I hoped that the Live CD would boot up and connect to the network confirming proper operation of the network jack.
Eventually I want to attempt dual booting this between OSX and Ubuntu.

Unrelated to the Ubuntu Live CD, a while back my router hung up and I could not log into it to change settings.  Caused my wireless devices to stop connecting but all wired devices still worked except for my daughters G4.  I flashed new firmware and got the wireless devices working again but her G4 would still not connect.  Her machine plugs in through a hub and the light on the hub never came on so it appeared that her network card may have quit.  When I tried hooking up the iBook I noticed that the hub light DOES come on for that port but she never gets an IP address.  It could be coincidence or perhaps there is something odd about the new firmware that requires something more for setting up a Mac.  Nothing I have seen documented though.

As for the Live CD, I am not ready to do a full install yet and just wanted to see if Ubuntu would load and connect to confirm hardware operation.  This iBook previously had another version of Ubuntu on it but I did not get an ID/Password from the previous owner so...
Perhaps I will try getting an earlier image like 6.01.

Thanks.

---

### Post by the_nite_owl on 2008-08-20
I did finally manage to get 8.04 to boot using the command combination: live-nosplash-powerpc video=ofonly 

Once booted I was unable to get a network connection so there is either something I do not know about Mac's and setting up DHCP with my router or the port is indeed dead.  Going to have to spend the money and order an airport card and see if it works that way.

---

### Post by cyberdork33 on 2008-08-20
just throwing this out there... you don't have MAC address restrictions setup on your router or anything do you?

---

