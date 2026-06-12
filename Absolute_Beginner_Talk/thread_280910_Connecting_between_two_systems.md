---
title: "Connecting between two systems"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by luken8r on 2006-10-20
I am looking to SSH between two PCs that I have, one desktop and one laptop. I can sucessfully SSH from one to the other, but how do I know which port it is using?  Is there a good way to list the used ports or open ports on either system?
The reason I ask is I cant seem to SCP a file from one to the other

First I log onto the remote system (laptop)

ssh <name>@<IP>

-=then

scp <local file> name@<IP of original PC>:/~/<new file>

When I do this, I get a connection refused error

---

### Post by glug101 on 2006-10-20
Likely, this is on port 22. (standard ssh port)  But, if you really must know for sure:

```
sudo apt-get install nmap
nmap *ip address*
```

Hope this helps:)

---

