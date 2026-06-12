---
title: "Security concern - gmail drafting and firegpg"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by yeehi on 2007-12-02
If I am writing something in gmail, and a lot of time is taken, it gets sent from my browser's text field to drafts, on the gmail server.
Is the text en clair, i.e. unencrypted, when sent?

Later, when I encrypt, and perhaps without my having made any modification to the draft, the exact same message is sent. 

It would be possible to establish my encryption passphrase from looking at the unencrypted and encrypted message, leaving all other messages I send/have sent with the same encryption key vulnerable.

is there a problem?

---

### Post by ubuntu27 on 2007-12-02
Are you using a client for e-mail or do you use webbased e-mail? 
If later, try loggin in with this URL [https://gmail.google.com](https://gmail.google.com)

Notice the "s" after the http protocol. Now everything is encrypted in Gmail :) 
Type that instead of the usual gmail.google.com  or just gmail.com

---

### Post by bluegreenwave on 2008-01-15
Yes, gmail does use ssl via https for secure login so all traffic would be encrypted. Protection may be afforded against anyone who might want to sniff in the middle, but once at gmail's servers the info is decrypted which allows curious third parties with access to gmail's traffic (i.e. law enforcement or government security agencies) access to such things as a saved draft which are not encrypted outside of the ssl algorithm. Can someone please verify this?
In my humble, and unsubstantiated opinion, I think it's best to encrypt/sign/etc the message BEFORE using gmail and then just copying it into the java field.

---

### Post by yeehi on 2008-01-23
I agree with your opinion. The Firegpg extension for Firefox enables you to encrypt in a dedicated text editor, prior to pasting it into gmail and then sending it.

Firegpg / firefox is a great way to do encryption on gmail.
I wish there were a similar feature for Opera...

---

