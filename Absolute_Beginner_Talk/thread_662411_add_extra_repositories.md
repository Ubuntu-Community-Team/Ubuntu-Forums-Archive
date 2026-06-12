---
title: "add extra repositories"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jaguar_jax on 2008-01-08
#

Most software repositories use a GPG key to digitally sign the files they provide, which makes it easy to check that the files have not been tampered with since their creation. In order for apt to be able to check this, you need the public key that corresponds to the signatures. The key should be available for download on the repository's website.
#

Once i get to this point I never get the GPG key to import?

---

### Post by WedgeHG on 2008-01-08
check out the man page for 'apt-key'

I think 'apt-key add filename' may be what you are after.


For an example of adding a repository see wine's at [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by overdrank on 2008-01-08
> **jaguar_jax said:**
> #

Most software repositories use a GPG key to digitally sign the files they provide, which makes it easy to check that the files have not been tampered with since their creation. In order for apt to be able to check this, you need the public key that corresponds to the signatures. The key should be available for download on the repository's website.
#

Once i get to this point I never get the GPG key to import?

HI and this link may help
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
When adding a repo under software sources there is a authentication tab and you can import the key there, Good luck!

---

