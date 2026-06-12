---
title: "Problem finding wine"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2006-09-27
A few people have been telling me that wine is in the repo, but I'm wondering if it has something to do with AMD 64.  Here's the process I'm going through.

sudo gedit /etc/apt/sources.list

open the file and add the listed repo deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main.

Acter that has been added and saved I run

sudo apt-get update

which returns the following errors

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
  404 Not Found
Fetched 4B in 3s (1B/s)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Where do I go from here?

---

### Post by pseudonym on 2006-09-27
Could mean that the repo server is down temporarily or having connection problems. It's been known to happen before. Just give it another shot later.

---

