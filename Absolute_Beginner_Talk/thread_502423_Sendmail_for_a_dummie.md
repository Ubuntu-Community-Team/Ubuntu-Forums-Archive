---
title: "Sendmail for a dummie"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by shallow on 2007-07-16
let me start off with all i want to do
im a Linux dummy i have to admit i enjoy GUI much more than CLI
new install of ubuntu i just want to run a wiki for me and about 80 other people.
i installed Mediawiki the wiki is up and running.
one problem when a users registers or looses there password they are supose to get an email
the system seems to be getting an email but in the Email log i get this

 Jul 16 16:35:32 localhost sendmail[7648]: l6GKZVbA007648: from=apache, size=711, class=0, nrcpts=1,  msgid=<200707162035.l6GKZVbA007648@bssb.com>, relay=apache@localhost
Jul 16 16:35:36 localhost sendmail[7649]: l6GKZWij007649: from=<apache@bssb.com>, size=922, class=0, nrcpts=1, msgid=<200707162035.l6GKZVbA007648@bssb.com>, proto=ESMTP, daemon=MTA, relay=localhost.localdomain [127.0.0.1]
Jul 16 16:35:36 localhost sendmail[7648]: l6GKZVbA007648: to=Rzwicker <rzwicker@bssb.com>, ctladdr=apache (48/48), delay=00:00:05, xdelay=00:00:04, mailer=relay, pri=30711, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (l6GKZWij007649 Message accepted for delivery)
Jul 16 16:35:36 localhost sendmail[7651]: l6GKZWij007649: to=<rzwicker@bssb.com>, ctladdr=<apache@bssb.com> (48/48), delay=00:00:00, xdelay=00:00:00, mailer=esmtp, pri=120922, relay=mail3.cocc.com. [204.60.84.2], dsn=4.0.0, stat=Deferred: Connection refused by mail3.cocc.com.


all i want to be able to do is have users log in and be able to reset there passwords and they get an email.
my guess is that sendmail is not configured correctly.
i have no idea how to do this. i have tried reading some of the things from a google search. but my eyes roll into the back of my head and i start to drool. i get so lost and confused.
i have a pop3 account that sendmail OR ANY OTHER software that would do this easly. 
any help from this drooling mess would be great

---

### Post by MrMercutio on 2007-07-16
If you have Wiki up and running, you should be running PHPMail as well. That is what you should be using, and not - if I understand you correctly -- your own POP-mail access. Now, a POP-service would be the safest and best, though. I don't know if you're hosting the wiki yourself or if you have a web host. Webhosts do however limit your mail bandwidth a lot of the time.

There should be a setting in Wiki (mind you, I'm not very well read on wiki -- except that it's a php-system and uses Mysql) that will allow you to send PHPMail which is a lot better than Sendmail.

About Sendmail vulnerabilities: [http://www.eweek.com/article2/0,1895,1941865,00.asp](http://www.eweek.com/article2/0,1895,1941865,00.asp)

About PHP-Mail: [http://www.scripts20.com/script/849/4633/phpmail.html](http://www.scripts20.com/script/849/4633/phpmail.html)

Now, all this is of course predicated on the fact that you're talking about the Sendmail-service of web hosts, and not about something else. You should really avoid sendmail. It is notoriously unreliable and unsecure, and you're just inviting trouble if you ever attract malicious users.

---

### Post by shallow on 2007-07-17
i honestly don't care what program i use to be able to have users receive there password emails
i will look into PHPMail. every one talked about sendmail.
i just want something easy to configure. 
yes i have my own pop3 account and i thought you should be able to add that into MediaWiki some how but i cant find it. i have tried posting on the MediaWiki forum but no answers.
i will looking into PHPMail and at the web site you sent me. 
hopefully this will work for me. cross your fingers

---

### Post by shallow on 2007-07-17
ok maybe i am missing other things
as i look over the mail text i posted here
it says its sending from sendmail but then there is something about apache

is it something i need to edit in apache or sendmail

i went to the phpmail web site you gave me thank you. i changed the settings in the php.ini file but there was no change in the mail log

that is why i asked about the apache and sendmail problem

---

### Post by shallow on 2007-07-18
is there a change i need to make some place
please im begging for help

---

### Post by shallow on 2007-07-19
there must be a simple answer for this. but as you can see from the title i am a dummie

---

### Post by shallow on 2007-07-25
any new ideas?

---

