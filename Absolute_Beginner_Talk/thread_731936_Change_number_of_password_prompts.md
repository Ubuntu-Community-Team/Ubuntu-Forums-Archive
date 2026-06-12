---
title: "Change number of password prompts"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2008-03-22
I am setting up ssh, and I want to only receive one password prompt for logging in. e.g. if I mistype it, I have to re-ssh in.

For the life of me I can't figure out where this is specified. Is this an ssh config thing, or a bash configuration, or ....?

I am using ssh keypairs for loging in if that makes a difference.

Andrew

Edit: **Solved**
For ssh logins with password, you can set "MaxAuthTries" to some number, where the login attempts will be n+1. This is specified in the ssh configuration file /etc/ssh/sshd_config
For ssh logins with keys, the key pass-phrase authentication happens on the client side, so it can't be controlled.

---

### Post by Patrick-Ruff on 2008-03-22
I'd like to know this as well.

---

