---
title: "gpg error messages"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-10-19
I'm trying to get Tor / Privoxy up and running. Anybody know how to fix the following?

mark@Lexington:~$ sudo gpg --keyserver subkeys.pgp.net --recv 94C09C7F
Password:
gpg: WARNING: unsafe ownership on configuration file `/home/mark/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
mark@Lexington:~$

and

without sudo:

mark@Lexington:~$ sudo gpg --keyserver subkeys.pgp.net --recv 94C09C7F
Password:
gpg: WARNING: unsafe ownership on configuration file `/home/mark/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
mark@Lexington:~$ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg: requesting key 94C09C7F from hkp server subkeys.pgp.net
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 3A skipped
gpg: invalid radix64 character 5F skipped
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 2D skipped
gpg: invalid radix64 character 3A skipped
gpg: invalid radix64 character 3B skipped
gpg: malformed CRC
gpg: read_block: read error: invalid keyring
gpg: Total number processed: 0

---

### Post by Mark_in_Hollywood on 2006-10-21
The difficulty was mine. I had not installed Tor before applying the next commands.

Tor/Privoxy is now up and running. Hooray.

---

