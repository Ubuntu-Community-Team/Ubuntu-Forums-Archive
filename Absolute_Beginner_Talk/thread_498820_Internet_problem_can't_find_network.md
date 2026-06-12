---
title: "Internet problem can't find network"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by sirad54 on 2007-07-11
Hi,
   Having problems with my internet connection. We had the power go out, so we lost internet connection. Re-established connection, wireless works fine but the ethernet connection from wireless router to desktop doesnt work. Directly connect laptop with XP to router, it works, copied ip address from laptop to linux machine under static ip address connection, linux machine doesnt work. Tried the same bypassing the router, failed same way. Used terminal to try to fix ( simmilar to ipconfig release/renew on windows) didnt work. tried simmilar methods with dhclient command in terminal, now getting "network is unreachable" error message. Please help me. I am afraid that my ethernet card has stopped working.

---

### Post by oilchangeguy on 2007-07-11
replacing a nic card in a desktop is an easy, and cheap fix. there's really no way to test the card. because even if the computer still sees the card, it may be bad.

---

### Post by sirad54 on 2007-07-11
But do you think that the card is bad or not?

---

### Post by oilchangeguy on 2007-07-11
> **sirad54 said:**
> But do you think that the card is bad or not?

like i said, there's no way to test the card (unless you have another desktop to try it in). do you have another ethernet cable you can try. if not, it seems your only choice is to purchase a new card. just make sure the stores return policy will allow you to return the card, if you need to. also try moving the card to another pci slot.

---

### Post by p_quarles on 2007-07-11
> **oilchangeguy said:**
> replacing a nic card in a desktop is an easy, and cheap fix. there's really no way to test the card. because even if the computer still sees the card, it may be bad.
I agree. It sounds like a power surge/interruption may have damaged the NIC, and it really is as simple as buying a new one for US$15 and plugging it in.

That said, I'll share a personal experience: my former desktop (now my server) always had a buggy NIC, or so I thought. When it gave out completely, I fooled around with it for a while and eventually discovered that the PCI bus connecting it the motherboard had a poor connection, ergo every time I moved the box, it got dislodged. I doubt that's the problem, but just make sure everything's plugged in tightly before buying anything.

---

### Post by sirad54 on 2007-07-11
I would like to exhaust all terminal options before purchasing a NIC card. Do you have anything to suggest or in your opinion is my card bad? I understand that I really can't test it, I was just wondering if you think that it is bad or were you offering that suggestion as the easiest.

---

### Post by oilchangeguy on 2007-07-11
> **sirad54 said:**
> I would like to exhaust all terminal options before purchasing a NIC card. Do you have anything to suggest or in your opinion is my card bad? I understand that I really can't test it, I was just wondering if you think that it is bad or were you offering that suggestion as the easiest.

did you read post #4?

---

### Post by sirad54 on 2007-07-11
okay, post 4 did not answer whether or not you thought the card was bad. To me it seemed that you were offering that suggestion as it would be what you would do. I am not ready to do that because I am still new to ubuntu and I might be able to fix it virtually rather than physically. Regardless of that miscommunication, do you have any suggestions/links to help me in the terminal? oh and if you read my original post I tried the same cable to a different machine, so all that worked, and I did forget to mention that I have removed and reseated all the cables and the card. I will try moving to a different PCI slot.

---

### Post by oilchangeguy on 2007-07-11
> **sirad54 said:**
> okay, post 4 did not answer whether or not you thought the card was bad. To me it seemed that you were offering that suggestion as it would be what you would do. I am not ready to do that because I am still new to ubuntu and I might be able to fix it virtually rather than physically. Regardless of that miscommunication, do you have any suggestions/links to help me in the terminal? oh and if you read my original post I tried the same cable to a different machine, so all that worked, and I did forget to mention that I have removed and reseated all the cables and the card. I will try moving to a different PCI slot.

the card probably is dead, and if it is, there's no magic command that you can enter in a terminal to bring it back to life.

---

### Post by Atomic Dog on 2007-07-11
Sounds like it may be dead.  Is it worth wasting hours when you can replace it cheap enough?

---

