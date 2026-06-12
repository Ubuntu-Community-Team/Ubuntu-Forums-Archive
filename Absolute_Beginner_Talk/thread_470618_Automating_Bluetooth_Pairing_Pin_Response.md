---
title: "Automating Bluetooth Pairing Pin Response"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by mhylmz on 2007-06-11
Hello,

I think this is the most suitable category for this post, so here you go:

I have Bluez and KDEBluetooth installed on my Ubuntu Feisty desktop. I'm sending files to my Bluetooth devices via certain Bluetooth applications.

I don't mandate pairing for my Bluetooth connections from my PC, however certain phones and PDAs do. Here's how it happens:

1.I send a file to my personal cellphone (Siemens SXG75).
2.My personal phone requests for a pairing PIN, I enter 1234.
3.Bluez-pin helper pops up, and requests for a pin, so I enter 1234.

Connection is then successful. 

If I do mandate pairing for my Bluetooth connections from my PC, this is what happens:

1. I send a file to my personal cellphone (Siemens SXG75).
2.My personal phone requests for a pairing PIN, I enter 1234.

Connection is then successful.

The problem with the second approach is, not all phones mandate pairing, and if I do turn on pairing, users of phones supporting non-paired connections will have to enter PINs to accept the files I'm sending. The problem with the first approach is I don't know how to automate the pairing PIN response.

I am aware that I can't know the PIN the user entered from his/her cellphone. But I should at least be able to send a "1234" response to any phone who wishes to pair with me at all costs :)

Does anyone have any info on this?
Best,
Mh Ylmz

---

