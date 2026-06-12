---
title: "Software Updates stopped working"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-29
I'm using dapper, and I can't update my software anymore. I get this error:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.9-0.0.ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread-escript_7.0.9-0.0.ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread-escript_7.0.9-0.0.ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.9-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.9-6.06dapper_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/mozilla-acroread_7.0.9-0.0.ubuntu0.6.06_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/a/acroread/mozilla-acroread_7.0.9-0.0.ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://wine.lowvoice.nl/apt/pool/main/w/wine/wine_0.9.30~winehq0~ubuntu~6.06-1_i386.deb](http://wine.lowvoice.nl/apt/pool/main/w/wine/wine_0.9.30~winehq0~ubuntu~6.06-1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)




I can't seem to find my sources.list file, either... Hmmm...

---

### Post by az on 2007-01-29
Your sources list is in /etc/sources.list and you need sudo to edit it.

But your problem is your proxy:
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by kbsuperstar on 2007-01-29
Oh yeah... I downloaded anon-proxy over the weekend. Maybe I should... remove it :D

---

### Post by kbsuperstar on 2007-01-29
I removed JAP, but the updates still won't work. I get the same error, hmm... Any ideas? Plus, I don't see my sources list where it should be..

---

### Post by Buck2348 on 2007-01-29
/etc/apt/sources.list

---

