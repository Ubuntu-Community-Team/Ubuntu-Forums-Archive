---
title: "SPAM Help"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by drhiii on 2008-02-26
I am connecting to an ISP that is letting a fair amount of SPAM through and I was wondering... is there any way to have some kind of service connection to this POP mailer and filter email, and then me download it from this third party?  Or, I have some Ubuntu servers... are there applications that will let me connect to this ISP and filter email, and then me connect to System #2 to pull it in?

tx

---

### Post by dcstar on 2008-02-27
> **drhiii said:**
> I am connecting to an ISP that is letting a fair amount of SPAM through and I was wondering... is there any way to have some kind of service connection to this POP mailer and filter email, and then me download it from this third party?  Or, I have some Ubuntu servers... are there applications that will let me connect to this ISP and filter email, and then me connect to System #2 to pull it in?

tx

My Evolution does more than adequate Spam ("Junk") filtering through the integrated Bogofilter system, there are also many other ways to filter junk but this is the simplest.

---

### Post by hyper_ch on 2008-02-27
if you operate your own mailserver you can filter out a lot of spam with the postfix anti-spam configuration options. Furthermore you can then use spamassassin and bayes on it. However, that's on a server level.

---

