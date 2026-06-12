---
title: "Oneiric/G4 PPC Powerbook: Unlikely - is there an issue with User Accounts Settings?"
date: 2012-01-12
forum: Apple Hardware Users
---

### Post by AndyHolyer on 2012-01-12
This is a bit of an odd one, and I'm checking to see if there is anything processor-specific before I ascribe my problem to personal slovenliness or similar.

Over the past few days, I've been putting Ubuntu onto a donated PowerBook G4. As expected this has faced a number of false starts, but I now have 11.10 running very nicely in general, and I'm just clearing up a few residual snags.

The one I was not expecting was in adding extra user accounts. I'd set up my own account during the installation process. Some point later, I tried to add an account for my son to use, and (more significantly) an account for the charity who actually own the box...
Going through the normal User Accounts control panel, all seems OK, except that no other accounts are ever listed the the left-hand list. Neither do they show up on the list of accounts on login.
Undaunted, (I've used Unix for 30 years), I go and dig around in /etc/ to see if I can do the same thing by editing /etc/{passwd,group,shadow.passwd etc}.

Still doesn't show the accounts in login window, which is a pity, also if I choose "Other" and log in like that, the Username shows up as "[Invalid UTF-8] in the top RH corner of the screen.

I just can't see how the processor could possibly affect this behaviour, but I thought I'd ask just in case.. Alternatively, I have not been able to find any docs of how Control-panel-installed user accounts differ from manually-added ones (some grepping around doesn't show me any difference).

Any hints gratefully recieved.

---

