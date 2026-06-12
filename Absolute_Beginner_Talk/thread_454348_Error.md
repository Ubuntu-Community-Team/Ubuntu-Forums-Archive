---
title: "Error"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-05-25
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Could someone exolain this to me?

---

### Post by aeiah on 2007-05-25
when getting wine, you downloaded a pgp key to verify that the file was authentic and not corrupted. synaptic (or apt-get) failed to match your key to the one on their server to verify this because it couldnt find the public key on their server, because its unavailable.

it may or may not cause any problems. you'll probably be ok.

---

### Post by burt_57 on 2007-05-25
> **aeiah said:**
> when getting wine, you downloaded a pgp key to verify that the file was authentic and not corrupted. synaptic (or apt-get) failed to match your key to the one on their server to verify this because it couldnt find the public key on their server, because its unavailable.

it may or may not cause any problems. you'll probably be ok.
Thank for fast response.

---

