---
title: "How Do You Decrypt Incoming GPG mail in Evolution?"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-08-23
Supposedly, it's GPG-supported with integral encrypt/decrypt, but for the life of me, I can't find how it decrypts an incoming GPGed message.

Thanks for any help.

---

### Post by jasmuz on 2005-08-23
Taken from the Evolution's help guide:

Unencrypting a Received Message

If you receive an encrypted message, you need to decrypt it before you read it. Remember, the sender must have your public key before they can send you an encrypted message.

When you view the message, Evolution prompts you for your PGP password. Enter it, and the unencrypted message is displayed.

---

### Post by polo_step on 2005-08-23
[QUOTE=jasmuz]
When you view the message, Evolution prompts you for your PGP password. [/QUOTE]
Yeah, I saw that too, but it doesn't.

It's like this feature is not in the Ubuntu version, or it doesn't recognize GPG (as opposed to PGP), or something.  You get an incoming encrypted message and it just sits there. No prompts, no error messages, nothing.  No recognition that it's an encrypted message.

Very mysterious!

Anyone actually get this to work in their installations?

---

### Post by polo_step on 2005-08-23
Oh, and I realize that there's a configuration entry in Edit>Preferences>Edit (Account)>Security for your eight digit GPG key number.

Assuming that's for your public key, I did that and rebooted with no improvement in the situation.

Still mysterious!

---

### Post by lothar_m on 2005-08-23
Thats odd.

when i receive a encrypted message evolution imediatly warns me and asks me for the password for decryptation.

Seems to work fine here.

Maybe you've got any misconfigured option in gpg..... Can you encrypt and decrypt files in your hard drive?

---

### Post by polo_step on 2005-08-23
[QUOTE=lothar_m]
Maybe you've got any misconfigured option in gpg..... Can you encrypt and decrypt files in your hard drive?[/QUOTE]

I'm not exactly sure what you mean.  I can en/decrypt from clipboard in kGPG anyway.

I use GPG with other programs with varying degrees of success, but I've never run it from command line.  As far as I can tell, it's configured correctly.  I have no idea how to configure the GPG program itself, only the configs in the various "shell" programs.

If I'm understanding the sparse explanations in the docs, all that's required to set up GPG in Evolution is to do the steps I mentioned in a post, above.  If I'm missing something there, please point it out.

The only thing I can see that I might have done wrong was to give the eight-digit Key ID of the *public* key instead of the *secret* key, as they don't specify, but the public key seems to be the most likely, as that's what was used to encrypt the message.

It's possible that I need to do something with the GPG program itself, but I don't know where to start. PGP 2.X (the most similar PGP to GPG) had virtually no configuration to do and I assumed GPG would be likewise.

---

### Post by nocturn on 2005-08-24
There are currently two standards for encapsulating OpenPGP messages, inline-pgp and pgp-mime, Evolution onlu support the latter.

You can recognise an inline PGP message easily, the PGP encrypted block is readable ASCII in the message block.

---

### Post by polo_step on 2005-08-24
[QUOTE=nocturn]There are currently two standards for encapsulating OpenPGP messages, inline-pgp and pgp-mime, Evolution onlu support the latter.

You can recognise an inline PGP message easily, the PGP encrypted block is readable ASCII in the message block.[/QUOTE]

OK...so then any message that looks like the one below will NEVER work in Evolution?:

-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.2.5 (GNU/Linux)

hQIOA6clhCMW6ndzEAgA5ML+xPvhegsiIGudxFcRYtM9kF8vXdMH86f6ahnlspQ/
+433rU7OnYTqzSWh9t8v7PET4WUMFpmRa5KzREDPGj2jJMOpjGMX8NXaNR2DWt5T
1PSfGMQJAtVdsc1IJKYO89VwyFyHKfHIBGEb5bP2tlvQ0B+c+ITb6/tml3EqJaXR
58A3EH9IYhM5KOFvo5a6m/VVTzbQjXVM6QdGHVTazg+zTiqQueqC0XtQ4phbjIkZ
wMtxXSddJL2k/ge5EBhIBxb9mUS/BwTFQ19icrryRr2vpV5sAfV+65e7zgsAERNC
sTmEpkW1T/4aBng4iM8SV/P+rIrtcMZMz6xArI3csggA4aQO4E8icmv92k0ULi+Y
ciXw0XSu8DmqYPRYdaC3BuzMb9IypCt2I4HBQv96IpwBMXVcmq/q4P5YAQoVG41p
Gc8R2ZjlPNH2LyTbIKIRvdC21qTTm5jsftnR2lXuI0E1ZlRmTTbnjJeYZ1BBcE4V
UN7jQaUNhwmVNIdDLV1wLS8h/1yOYhG2Xel3wPaZY323ipVVwFyZsTRAv8VLKSNa
ATcPMXgc25IVEWUW+c4HBNeugaHy6VUgOWyTfkgUz8JHdEWASkbaREvcPvA7wFGE
FhnW7+UzzREnvZm/ImCF+8tFpt7wOD8nrGPY/hhUBlW5U1uuul1lhKIcJckGWJ34
i9J9AcoDBS5Ukx17eodtFiSEfNblxpHyDPC9f2ea0U6a5fCH/Q65VhbriSLlPhCO
Sv3XIgsfeXLbRmM1h2fiYmxWefUNSglZO84mwDJM5Tr0LevQS/uDUWLu6EJ0sb3q
BRT262va1/4ACHF3gBlVxUzBC8+UHcu1QGIMqnLj0Go=
=Zwlb
-----END PGP MESSAGE-----

---

### Post by nocturn on 2005-08-25
[QUOTE=polo_step]OK...so then any message that looks like the one below will NEVER work in Evolution?:
[/QUOTE]

They probably will, I believe inline PGP support is being added to evolution in Breezy (or +1).
It was left out because the specification is not consistent.

You can decrypt it with another utility too (like gpa, seahorse, ...) or just use the command line.

Save the message to a text file,
```

gpg --decrypt <textfile>

```

---

### Post by doclivingston on 2005-08-25
[QUOTE=polo_step]OK...so then any message that looks like the one below will NEVER work in Evolution?:[/QUOTE]

[The Gnome bounties page](http://www.gnome.org/bounties/Mailer.html#127521) lists that as "solved", and the referenced bug notes that it was included in Evolution 2.3.4 - so it'll be in Breezy.

---

### Post by polo_step on 2005-08-25
[QUOTE=doclivingston][The Gnome bounties page](http://www.gnome.org/bounties/Mailer.html#127521) lists that as "solved", and the referenced bug notes that it was included in Evolution 2.3.4 - so it'll be in Breezy.[/QUOTE]
OK, so it's a bug and I'm not crazy.

That's a relief.

I'm still struggling to find a functional mail client.  I detest Thunderbird worse than any program in recent memory, and Evolution is going to choke on GPG even worse than Thunderbird does...so what are some good alternatives?

What I want is fairly simple GPG support, service for multiple accounts and an editor that doesn't force all sorts of junk on me (like Thunderbird's gawdawful, troublemaking quote bars) the way most do.

Is Balsa any good?  Any other recommendations?

As always, thanks for any help!

---

### Post by nocturn on 2005-08-25
[QUOTE=polo_step]OK, so it's a bug and I'm not crazy.

That's a relief.

I'm still struggling to find a functional mail client.  I detest Thunderbird worse than any program in recent memory, and Evolution is going to choke on GPG even worse than Thunderbird does...so what are some good alternatives?

What I want is fairly simple GPG support, service for multiple accounts and an editor that doesn't force all sorts of junk on me (like Thunderbird's gawdawful, troublemaking quote bars) the way most do.

Is Balsa any good?  Any other recommendations?

As always, thanks for any help![/QUOTE]

Evolution has excellent GPG support, the pgp-mime standard has been arround for ages and is vastly supperior to inline-pgp sot it makes sense to use it.  I'm surprised that not more clients use it by default.

---

### Post by polo_step on 2005-08-25
[QUOTE=nocturn]Evolution has excellent GPG support, the pgp-mime standard has been arround for ages and is vastly supperior to inline-pgp sot it makes sense to use it. [/QUOTE]
[sigh!]

OK...

1) I've been warned elsewhere NOT to use PGP-MIME in this stuff for some inscrutable reason, but...

2)  I have no idea whether it's configured for GPG/PGP-MIME anyway.

How can I tell?

I see no configuration for it in Evolution.

Do I do it somehow in GPG's configuration (wherever it is) and if so, how?

Thanks for any help.

---

### Post by nocturn on 2005-08-25
Maybe this will help:
[http://www.novell.com/documentation/nld/index.html?page=/documentation/nld/evolution/data/encryption.html#encryption](http://www.novell.com/documentation/nld/index.html?page=/documentation/nld/evolution/data/encryption.html#encryption)

---

### Post by polo_step on 2005-08-27
[QUOTE=nocturn]Maybe this will help:
[http://www.novell.com/documentation/nld/index.html?page=/documentation/nld/evolution/data/encryption.html#encryption](http://www.novell.com/documentation/nld/index.html?page=/documentation/nld/evolution/data/encryption.html#encryption)[/QUOTE]
I see nothing in there that addresses the problem.

I'm not saying that it positively isn't there, but I sure don't see it if it is.  According to this, GPG should be working with my Evolution mail program, and it doesn't...which is where I came in here.

---

### Post by polo_step on 2005-08-30
Translating things into PGP language (after poking around on the bugsites), it appears that Evolution does not support ASCII-Armored (-eat) messaging.

Surprising, as this is what virtually everyone with PGP has exclusively used for e-mail.for years.

Brilliant.

---

