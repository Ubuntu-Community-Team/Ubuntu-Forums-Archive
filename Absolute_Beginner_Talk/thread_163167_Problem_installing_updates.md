---
title: "Problem installing updates"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-20
Hi,
I've got 13 new updates, but I can't install them,
When I press install it does whatever it does, and the comes up with the message
"Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?"

I click "yes" and it comes up with an error messsage:
> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.6.1-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.6.1-0ubuntu1_i386.deb)
  Bad header line [IP: 85.133.25.7 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-exchange/evolution-exchange_2.6.1-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-exchange/evolution-exchange_2.6.1-0ubuntu1_i386.deb)
  Bad header line [IP: 85.133.25.7 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/example-content/example-content_10_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/example-content/example-content_10_all.deb)
  Bad header line [IP: 85.133.25.7 80]

What does it mean?

Thanks,
Josh:)

---

### Post by sYs^ on 2006-04-20
Did you try any other servers? Try removing gb. from your /etc/apt/sources.list then sudo apt-get update and try upgrading again.

---

