---
title: "Max bandwidth user by logs"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by adityaj on 2008-02-29
Hi

I have at my disposal a tcpdump/tshark log of an active ethernet connection. By looking at the log (assuming it has all the requisite protocol fields) how can i determine the node using the most bandwidth. My idea is:

1. For each source ip add the outgoing tcp packet lengths
2. For each destination ip add the  outgoing tcp packet lengths
3. For each ip add its (incoming, outgoing) value 
4. Sort in descending order

This sound ok? Or have i missed something?

Regards

Aditya

---

### Post by ruy_lopez on 2008-02-29
"tcptrace" should simplify your effort. Just run it against a tcpdump file and it'll output a summary.

---

### Post by drubin on 2008-02-29
Does it have to be logs?

Or could you use Ipcop(linux fire wall)?

---

