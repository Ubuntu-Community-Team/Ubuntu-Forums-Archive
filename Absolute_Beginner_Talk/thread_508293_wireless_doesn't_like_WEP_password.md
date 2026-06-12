---
title: "wireless doesn't like WEP password"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by BeardedOne on 2007-07-24
Frustrated with my onboard rt2500 wireless chipset, I bought an AirLink 101 card with an Atheros chipset.  With it, Ubuntu 7.04 (booted from CD) detects my router reliably.

The problem
I try to connect and a window asks for a password (my router is set to WEP-Open).
If I select WEP-Ascii and type my ten digits, the login button doesn't light up.  I'm stuck.
If I select WEP-Passphrase and type the same number, the login button lights, but there's no connection.
If I disable security on my router, it connects with no problem.

What's the deal with the password window?
(yes, I've triple checked my password number and connected with that number through windows)
(yes, I need to keep my security in place)

So close, and yet, so far.

Thanks

---

### Post by ugm6hr on 2007-07-24
Not sure if this will help, but when I used Network Manager, I was only able to get a HEX WEP key to work.

Now I use Wicd instead, because it is more stable with madwifi and WPA (but Network Manager worked perfectly with WEP).

---

### Post by BeardedOne on 2007-07-24
Thanks.

Ok, this is weird - 

So I typed in the WEP password in HEX and it didn't light up the login button.

BUT, when I chose WEP-HEX in the password window and typed the passwood in ASCII (yes, you'll try anything at 3am with a busted wireless), it worked fine.

I don't know why this is so, and will just go with it, but it's weird.

The bottomline - on an Averatec 3225, using an Airlink 101 card with Atheros chipset and the HAL Atheros driver (which signaled it was 'restricted' when I booted up) you type the ASCII password in the WEP-HEX slot.

---

### Post by ugm6hr on 2007-07-24
At least you're online now...  Pleased it's sorted.

---

