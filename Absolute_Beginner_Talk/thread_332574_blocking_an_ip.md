---
title: "blocking an ip?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2007-01-06
Does iptables block an IP address for everything including SSH access through such as putty?

---

### Post by steve.horsley on 2007-01-06
That depends on the rules fed into iptables. The simplest rule would be one that blocks all protocols to the address, but it's all optional. **sudo iptabes -L** will show you the current rules.

---

