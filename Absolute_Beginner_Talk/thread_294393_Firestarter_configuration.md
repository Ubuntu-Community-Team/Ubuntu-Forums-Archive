---
title: "Firestarter configuration"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Tyx on 2006-11-06
Hi,
Can anyone tell me how to configure firestarter so that it 
allows a whole domain to ssh to it?
I mean, if my pc is e.g. dapper.ubuntu.co.uk, which is allowed 
by firestarter, how can I allow my friend's pc, edgy.ubuntu.co.uk,
or for that matter, the entire ubuntu.co.uk domain, access?
(I don't want to make a separate rule for each ip address)
Thanks.

---

### Post by wieman01 on 2006-11-07
The answer is to open "inbound traffic" for "anyone" (port 22). See screenshot...

But remember that this opens the SSH port to any parts on the web. So a good password protection (or via certificate) would be healthy.

---

### Post by sbassett on 2006-11-07
Along with editing your /etc/hosts.allow

```
sshd: .ubuntu.co.uk : ALLOW
```

and also placing the following within /etc/hosts.deny

```
sshd: ALL : DENY
```

If there are any other hosts that would require access to ssh, be sure to allow them as noted above within the /etc/hosts.allow.

---

