---
title: "Network Manager uses Keyring and asks me for WPA?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Ozor Mox on 2007-03-23
Why does Network Manager store my WPA network key in the Keyring Manager and ask me for the Keyring password every time the computer starts up if it is still going to ask me for the WPA? Sometimes it asks two or three times before finally connecting, and sometimes after typing in the WPA it gives up and I have to initialise it manually.

Is this because of a low signal (it's reporting 78% right now, is that low?) and the Network Manager is timing out when attempting to connect, or is this a quirk of some kind? Would anyone advise I try WICD instead?

---

### Post by joethenoob on 2007-03-23
I've had a similar problem, tho not as severe as this. Maybe one of the ubuntu l33t can clue us in, but I thought it worked like this:

The first time you connect to your wifi network with networkmanager, it prompts you for the WPA password. Once  you enter it, the WPA password gets stored in the keyring. The first time you use the keyring (which for me was when I first connected to my wifi),  you are prompted to enter a password for the keyring application. The keyring password doesn't have to be the same as your WPA password.

When you connect to the wifi network, networkmanager tries to get the WPA password fromt the keyring, but in order to access the keyring you need to enter the keyring password. Is your head spinning too?

I guess teh keyring manager will be a nice utility once you are using it to store different passwords for different thing. But when the only thing that is using the keyring is networkmanager, it seems kind of redundant to enter one password just so netman can access another.

Can anyone tell me (1) how far off I am and (2) how do we disable this if we're only using the keyring for one password? Keyring best practices maybe?

k thx bai

---

