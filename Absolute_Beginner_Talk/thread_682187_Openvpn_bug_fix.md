---
title: "Openvpn bug fix"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by wak_wak on 2008-01-29
If you're running in to this message when trying to connect with KVpnc:

debug: "openvpn" started.about:blank
info: Successful connect try canceled.

Use this fix:

simply added the following commands to the "Before Connect":
rm /bin/sh
ln --symbolic bash /bin/sh

and the following commands to the "After Disconnect":
rm /bin/sh
ln --symbolic dash /bin/sh

There appears to be a bug with it and Gutsy which is at least temporarily fixed with the above.

Here is the URL where I found that:
[https://bugs.launchpad.net/ubuntu/+source/kvpnc/+bug/118847](https://bugs.launchpad.net/ubuntu/+source/kvpnc/+bug/118847)


Good luck:)

---

