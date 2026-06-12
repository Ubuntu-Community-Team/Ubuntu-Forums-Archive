---
title: "isp's smtp not secure?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-08-03
Hi 
I'm using Shaw internet from Vancouver and it block's e-mail providers' smtp (like gmail.com). So then I tried to use their own server which is shawmail.vc.shawcable.net. 
However, it only works with no encryption and does not use any security protocol like SSL or TLS, which I'm not comfortable with. 
Is there any way around? or perhaps use some other 'global' server which they wouldn't block.

Thanks

:-)

P.S: This occurs with any email client - evolution, thunderbird or outlook; so it shouldn't be related to the email client.

---

### Post by asmoore82 on 2007-08-04
it's very common for ISPs STMP or POP servers to be unencrpyted
because they only allow people to access it from inside their WAN.

---

### Post by HermanAB on 2007-08-04
SMTP is by design unconcerned with the security of the data that it transports.  If you wish to secure email, then you have to use encryption at the endpoints.  However, SMTP (since it is is on top of TCP) is concerned about the integrity of email and any message sent should arrive at its destination unmodified.

As pointed out above, ISPs limit access to their servers in several ways, including POP before SMTP and ensuring that only their own users can relay mail via their servers.

---

### Post by genbuntu on 2007-08-04
So does that mean that I don't have to worry about someone snooping on my sent mail.
Would it be as safe as using a browser to check email?

---

### Post by HermanAB on 2007-08-04
It is difficult for ordinary users to snoop on your mail, however, the technicians at any one of the unknown number of servers a long the way that the message has to travel can easily snoop on your mail.

Basically, email is as secure as a postcard, with the added problem that being in electronic form, it is never really erased and can haunt you forever.  So it is somewhat like post cards written in indelible ink nailed to a tree some ways off the ground, in some public parks and you don't get to know which public parks.

The only safety you have, is safety in numbers, but 'grep' can cut through the crap very easily.

If you are really worried about security of your email, then you have to encrypt it end to end which requires collaboration with the receiver.

'Hope that helps!

Herman

---

### Post by nitro_n2o on 2007-08-04
there is a free encrypted email [www.hushmail.com](www.hushmail.com) this might help get some privacy

---

### Post by genbuntu on 2007-08-04
lol! the analogy with postcard was good. 
So from what I understood was that my email's safety can be sacrificed even when not using e-mail clients but by using them I'm adding another 'tree' on which my 'postcard' can be pinned. 
Its not that my emails are like 'agent 007's secrets but this issue originated out of a concern of my password being leaked out if I use unencrypted smtp; as opposed to using a web-browser.

:)

---

### Post by HermanAB on 2007-08-04
Many protocols use plain text for username and password exchange:
FTP, POP, IMAP...

SMTP doesn't actually use authentication at all!

The important thing is to ensure that you use separate usernames and passwords for the insecure protocols.  Don't use the same ones for important stuff.

---

### Post by genbuntu on 2007-08-05
I see now. checking one's email is  much more unsecure than I initially thought.
thanks

---

### Post by HermanAB on 2007-08-05
Yup, if you use POP or IMAP, then your email client sends your username and password in plain text to your ISP every 3 minutes or so:

Username/Password Sniffing for Fun and Profit:

I frequently have to fix someone's email setup and the user invariably has no friggen clue what his username and password is. Most people use plain text POP3 or IMAP4, so if it still sort-of works, then you can put a Linux notebook machine on a hub and sniff the information.

To do this you need 'ngrep'. Do 'urpmi ngrep' if you don't have it, then try these two commands, while clicking the 'Check Mail' button in the mail client, or just wait a few minutes for the auto check to trigger:

# ngrep -q "user"
# ngrep -q "pass"

La Voila!

Most people use the same username and password for everything and if this doesn't convince them that it is a bad idea and that you should never read mail as 'root', nothing will...

BTW, you can also use tcpdump and grep - just a little more convoluted:
tcpdump -s 256 -A -i eth0 | grep -i user

Cheers,

Herman

---

### Post by steve.horsley on 2007-08-05
> Do 'urpmi ngrep' if you don't have it,
But if you're on Ubuntu instead of Mandriva, you should use
**sudo apt-get install ngrep**
instead. :)

---

### Post by HermanAB on 2007-08-05
Heh, that was a cut'n paste from another guide of mine.  Good catch!

---

