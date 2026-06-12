---
title: "1 pc, 1 mac, 1 server. possible?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by cypher1313 on 2007-07-15
Hey guys,

Just registered, great community you have here.

I'm a total n00b when it comes to linux, but i've already learnt a lot here in the last two hours or so, just browsing. Obviously, i'm looking into Ubuntu, and i'm pretty sure I can manage installing.

But before I do let me just fill you in on my situation:

I'm using a PC laptop, my room mate is using a mac. We also have an older PC that we're turning into a file server. We're planning on running windows  server 2k3 on the old machine as a good friend of mine owns a hosting company and gave us a copy. Ideally what we'd like out of this "server" is to share music, files, general file storage, printing capabilities and eventually in the future as an additional firewall.

I was just wondering what you guys foresee as any potential problems, or how I should go about setting this up. I'd like to partition my HD so I can use windows and/or Linux.

Thanks

---

### Post by starsky on 2007-07-15
> **cypher1313 said:**
> Hey guys,

Just registered, great community you have here.

I'm a total n00b when it comes to linux, but i've already learnt a lot here in the last two hours or so, just browsing. Obviously, i'm looking into Ubuntu, and i'm pretty sure I can manage installing.

But before I do let me just fill you in on my situation:

I'm using a PC laptop, my room mate is using a mac. We also have an older PC that we're turning into a file server. We're planning on running windows  server 2k3 on the old machine as a good friend of mine owns a hosting company and gave us a copy. Ideally what we'd like out of this "server" is to share music, files, general file storage, printing capabilities and eventually in the future as an additional firewall.

I was just wondering what you guys foresee as any potential problems, or how I should go about setting this up. I'd like to partition my HD so I can use windows and/or Linux.

Thanks


Hi there :)
welcome to ubuntu forum :)

Yes, you can do this setup for file server on Win2k/XP/Vista.

Look up for samba and cifs -
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

On mac, you'd probably have to follow similar path. They are -
1. Install samba
2. Make necessary modifications to configuration files.
3. Mount the remote windows machine.

HTH

---

