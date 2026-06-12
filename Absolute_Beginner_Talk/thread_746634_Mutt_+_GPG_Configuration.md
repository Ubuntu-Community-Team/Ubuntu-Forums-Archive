---
title: "Mutt + GPG Configuration"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-04-05
Greetings,
I have mutt setup on my server to send and receive mail, I copied my .gpg directory over to there, so I can sign / encrypt / decrypt messages in mutt, and have added the following to my .muttrc file:

```
set pgp_decode_command="gpg %?p?--passphrase-fd 0? --no-verbose --batch --output - %f"
set pgp_verify_command="gpg --no-verbose --batch --output - --verify %s %f"
set pgp_decrypt_command="gpg --passphrase-fd 0 --no-verbose --batch --output - %f"
[B]set pgp_sign_command="gpg --no-verbose --batch --output - --passphrase-fd 0 --armor --detach-sign --textmode %?a?-u %a? %f"
set pgp_clearsign_command="gpg --no-verbose --batch --output - --passphrase-fd 0 --armor --textmode --clearsign %?a?-u %a? %f[/B]
set pgp_encrypt_only_command="pgpewrap gpg --batch --quiet --no-verbose --output - --encrypt --textmode --armor --always-trus
set pgp_encrypt_sign_command="pgpewrap gpg --passphrase-fd 0 --batch --quiet --no-verbose --textmode --output - --encrypt --s
set pgp_import_command="gpg --no-verbose --import -v %f"
set pgp_export_command="gpg --no-verbose --export --armor %r"
set pgp_verify_key_command="gpg --no-verbose --batch --fingerprint --check-sigs %r"
set pgp_list_pubring_command="gpg --no-verbose --batch --with-colons --list-keys %r"
set pgp_list_secring_command="gpg --no-verbose --batch --with-colons --list-secret-keys %r"
set pgp_autosign=yes
set pgp_sign_as=0x26FD8AF9
set pgp_replyencrypt=yes
set pgp_timeout=1800
set pgp_good_sign="^gpg: Good signature from"

```

Yet when I sent a test email to my other email address, it signed the message, yet the PGP signature was an attachment! I was wondering what was causing this behavior, and if there was a simpler way to have it, so it would send it like:

> -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1



This would be a sample message.


-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFH+Ac0vJhQqSb9ivkRAq/GAJsGehcsdRvZq4tomzcDBEb2aEpQ9QCdEWHl
+fGafgaupACKThGDtF5VbTo=
=Stus
-----END PGP SIGNATURE-----


If you take a look at the options in the .muttrc, especially the two in bold, I think that is what is causing my signature to be attached as an attachment. Can anyone enlighten me, as to how I should fix this?

Dr Small

---

