---
title: "what now?"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Cyraxzz on 2006-10-26
In the middle of the distro upgrade(with gksu "update-manager -c"), i received an error message stating that it could not connect to a certain server. It could not continue the installation.

I edited the source list by replacing "Dapper" with "Edgy" and typed the following command "sudo apt-get dist-upgrade" it responded with "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by ewl1217 on 2006-10-26
Update with the following command:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

