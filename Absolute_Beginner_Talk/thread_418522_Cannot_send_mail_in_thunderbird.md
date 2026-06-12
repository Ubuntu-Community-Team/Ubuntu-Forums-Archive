---
title: "Cannot send mail in thunderbird"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-04-22
I'm trying to send mail with enigmail in thunderbird 2.0 and enigmail 0.95.0. I have a public key that was created with enigmail in thunderbird 1.5 and works fine, I can sign and encrypt without any problem (it does require a passphrase to use this key), but in 2.0 I never even get prompted for my passphrase, it immediately goes to this error:
```

Error -- bad passphrase

gpg command line and output
/usr/bin/gpg --charset UTF8 --batch --no-tty --status-fd 2 --clearsign -u 0x6DCA6F17 --use-agent
gpg: problem with the agent - disabling agent use
gpg: can't query passphrase it batch mode
gpg: invalid passphrase; please try again...
gpg: can't query passphrase it batch mode
gpg: invalid passphrase; please try again...
gpg: skipped "0x6DCA6F17:" bad passphrase
gpg: [stdin] clearsign failed; bad passphrase

```

I think it might have something to do with the --use-agent. I have the use agent option disabled though so I don't know why it's there. Anyone have any ideas for me?

---

### Post by IamAcoconut on 2007-10-23
I had the same issue. I had to uncheck a box next to "never ask for a passphrase" in **Enigmail settings**, although I never checked it, TB upgrade seems to have sth to do with it.
I also installed package called **pinentry**-gtk2, as recommended on other forum.
How did you solve the problem?

---

