---
title: "Serial modem trouble"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by DPMR on 2006-11-19
I have search the Wiki for information on this but it is not real clear as to what some of the meanings are.

I am getting the modem to dial and lessoning to it's speaker, it is dialing the right number.

But it is not making the connection. I assume it is a problem with info i have put in the settings interface but I can seam to figure out what it is.

Some of the entries I'm not sure if I understand what it is it wants me to enter.

Is there any docs that would explain what each entry is?

---

### Post by foxmulder881 on 2006-11-19
Can you maybe contact your ISP and ask them what it may be? If it dials and the number is right, there shouldn't be a problem.

Just a question for you too, any reason why you're still using a serial modem?

---

### Post by DPMR on 2006-11-19
Well being a newbie I still use Windows. And I don't have any trouble using the modem there, so I assume it must be the way it is setup in Ubuntu.


I use to have a lot of trouble in Windows with programs launching off to the internet. So I liked the fact that I could just push a button and stop the traffic.

---

### Post by foxmulder881 on 2006-11-19
Firewalls have a 'Stop Traffic' button if that's any help for a future modem upgrade.

---

### Post by confused57 on 2006-11-19
You might want to try wvdial, as described here:

[https://help.ubuntu.com/community/DialupModemHowto#head-cdd16131926f734c4736b833b907c8fb24478187](https://help.ubuntu.com/community/DialupModemHowto#head-cdd16131926f734c4736b833b907c8fb24478187)

---

### Post by DPMR on 2006-11-19
Thanks confused57

I have been trying what is there.
I guess I just have to go over it a few more times.

---

### Post by foxmulder881 on 2006-11-19
Or maybe your old serial modem doesn't like Linux that much perhaps?

---

### Post by randiroo76073 on 2006-11-19
Foxmulder881, what would you have us use on dial-up, serial modems[aka: external modem] are the most easily recognized modems in linux, where-as winmodems[aka: internal modem] are harder to make compatable in linux, especially for newbies.  Unfortunatly not everyone has DSL,cable,satellite available or can afford.  Do you have a better answer?

DMPR, can you give a little more info, what modem are you using?  Ie:  make, model# ?  Calling ISP is a good idea to double check info.  I have a serial modem too and didn't experience that much problem.

---

### Post by foxmulder881 on 2006-11-19
Why am I getting flamed? All I asked was why was he still using a serial modem. Simple question. I don't care whether he is or not. And I was simply suggesting he upgrade in the near future as serial modems will only be supported for so long. Many mobos don't even have serial and parallel ports anymore. And I was surprised that someone was still using one.

---

### Post by towsonu2003 on 2006-11-19
> **foxmulder881 said:**
> Why am I getting flamed?

most probably because your question isn't helping him / her, but instead it's decreasing his/her chances to get adequate help as the number of replies increases (ppl will think s/he is getting good help as the # of replies increases, which is not the case here). ;)

I wonder if the OP tried wvdial. What was the output? randiroo's question might also get others using the same hardware to help (I would post modem info **bold**ly) Also, what's your ISP?

---

### Post by PennYanPete on 2006-11-19
Hi DPMR

I am also stuck with dial up and had a similar 
problem the other day. If you have onboard etho
go into bios and disable it. Just something
simple to try, if it doesn't help, go back
and enable it. It (etho) will be visible in the
modem configure window. This worked for me.

PYP

---

### Post by randiroo76073 on 2006-11-19
foxmulder881, sorry if you felt it was a flame,actually it was a question in your haste you missed.
Did we lose DPMR?  Hope not.

---

### Post by foxmulder881 on 2006-11-21
That's alright randiroo76073. No harm done.

---

