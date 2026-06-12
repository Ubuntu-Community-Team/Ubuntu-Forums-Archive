---
title: "no  email"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by alanc on 2007-07-01
:p  Hi.   I am trying to set up evolution mail, but when i click on send & receive i get this:
        No route to host.  Could someone please explain to me  where i have gone wrong.
                                                     Regards     alanc:(

---

### Post by p_quarles on 2007-07-01
I'll try, but first you'll have to describe what you've attempted so far.

---

### Post by alanc on 2007-07-03
:p Hi.   I haven,t tried anything really, i have just installed Ubuntu 7.04, and evolution was on the disc.
                                      Regards   alanc:p

---

### Post by farueulogy on 2007-07-04
so you haven't setup your account or anything?

have you used an email client before or do you normally just go into a webbrowser (eg firefox)?

what mail service are you using (eg hotmail, yahoo, gmail)?

---

### Post by alanc on 2007-07-10
:) Hi.    No, i haven,t set up an account as yet, don,t know where to start. I have been using Outlook
           Express in windows XP. Hope that is all you require.
                                                                Regards    alanc::(

---

### Post by Ek0nomik on 2007-07-10
Who is providing you with your e-mail service?  Gmail, Hotmail, Yahoo, Charter, Roadrunner, work (ex: [email]my.name@fedex.com[/email], [email]my.name@sony.com[/email], etc)

If it is a public offering like Gmail, getting it setup should be a breeze.  If it is your Internet Service Provider (ISP) or work employer, it may be a little more tricky.  If it is the latter, you will need to get some server information from them.  Whether they use POP or IMAP, and the relevant information, and the SMTP information.  (I don't mean to scare you.  ;))

Just let us know who is providing your service (what is your e-mail address essentially), and we can move on from there.

---

### Post by farueulogy on 2007-07-10
Actually - Assuming you still have your windows partition with outlook on it - **If you go into windows and open outlook from the menus (file, edit, view etc...) you could find preferences/options/accounts and find all your information from there.**

I never use outlook so I'm unsure quite where you'd find it. Have a good look around. You need to find out:

The server type: This is most probably something called "pop3" or "pop" but it could be Hula, IMAP, Microsoft Exchange or a whole number of things.

The server address: Something along the likes of pop.gmail.com - Obviously I wont look like this if you server type is IMAP or something else.

Your username for the mail account - Posibly your email but not always.

Your password from the mail account.

Whether your account has SSL or TLS security on it.

Your SMTP server name eh smtp.gmail.com. SMTP is the bit of email which lets you send mail.

Your SMTP username and password - Which can be different or the same to your "pop" or other username or password. More likely it is the same.

Make a note off all this from your settings you look up in outlook on windows and when you get across you'll have a good chance of getting set up.

There might be an issue with port numbers but since you're setting up evolution which I'm checking right now and I can't even find where to put in port numbers - We'll assume it's ok for now.

---

### Post by alanc on 2007-07-15
:o  Hi.   Thank-you, i have it all set up and running now.
                               Regards     alanc:)

---

