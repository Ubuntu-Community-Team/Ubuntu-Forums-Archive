---
title: "New to gnome"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by highneko on 2006-10-04
Hello. I'm new to gnome and have been trying to make it look all nice and pretty!

When I put my mouse over things this little popup thing appears, I think it's called a tooltip, how do I get rid of all these? I've been reading but can't find any information on this.

I'm also wondering how to get rid of the window outlines when minimizing. I found some information about removing the outline when programs are started, but not for minimizing.

gconf-editor isn't very helpful with this stuff. I just installed ubuntu yesterday, and it's my first time using gnome.

Thanks for your time! :3

---

### Post by sbergman27 on 2006-10-04
Well, the only way I know of is in gconf-editor:

apps->metacity->general->reduced_resources

That also gets you wireframe window moves, etc. so you may or may not not like it.

---

### Post by highneko on 2006-10-04
[QUOTE=sbergman27]Well, the only way I know of is in gconf-editor:

apps->metacity->general->reduced_resources

That also gets you wireframe window moves, etc. so you may or may not not like it.[/QUOTE]
At first I didn't like the wireframe, but later figured out how to remove the wireframe effect.

Boolean true;
/apps/metacity/general/reduced_resources
Boolean true;
/desktop/gnome/interface/accessibility

Thanks alot. Maby someone can help me with the tooltip problem now? I would have a great gnome!

---

