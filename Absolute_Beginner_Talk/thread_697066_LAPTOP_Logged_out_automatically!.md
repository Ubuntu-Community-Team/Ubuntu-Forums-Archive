---
title: "LAPTOP: Logged out automatically!"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-14
Remember the turned off issue I am experiencing a few days ago? Well I experienced it ago.

I have to corrent it, the computer **does not turn off**, instead it automatically logs me off, seeing the black thing again, with of course a message like job cron something, sometimes it hangs sometimes it doesn't

Weird, tried experimenting it, using **userspace**, with a **performance_ac** of **85**, and then lowered to **75**, still it logged off automatically,

Now, tried ondemand, with a **performance_ac** of **85**, and then lowered to **75**, still the same results.

Really really weird, I don't think this can overheat the laptop, since I don't usually reach to **1.70GHz** ...

Before logging off automatically, I always see a blank screen, something like there's a message that **ACPI** not supported or **Asus** **Asus** messages which is weird because I am using an **Acer Laptop**.

HELP!!!:confused::confused::confused::confused:

I am already contented with **Linux**, I wanted to have a wonderful experience while using **Ubuntu**, without this error.

**POWER TALK**: > The Plan to avoid the logged off automatically thing... will just apply in a few minutes...

To be sure, I set my power to userspace via cpufreq-set and then the minimum is **600MHz** and the maximum is **1.40GHz** ...

It works, but only, there is a problem, everytime I restart, It returns to **ondemand** or **userspace**, but without the** 600Mhz-1.40GHz limit**, instead, there is no limit.

**600Mhz-1.70GHz** ... I am sacrificing my computer performance to avoid the automatic shutdown/logged off thingy...

Please help me. Please.:confused:

[b]I am pretty sure as far as I can remember, it's an ACPI error ... Here are the screenshots... Help!!! Really need it.

Please also define the following: userspace ondemand powersave nothing conservative and performance_ac and performance_battery ... explain and define using friendly words... help help help!:confused:

I also attached the log files for you to analyze. Please help me, there must be a bug!:confused:

---

### Post by tribble222 on 2008-02-15
I'd like to help but I'm having a lot of trouble undertanding your writing, especially with all the bolded words and no paragraphs.

---

### Post by karlo on 2008-02-18
> **tribble222 said:**
> I'd like to help but I'm having a lot of trouble undertanding your writing, especially with all the bolded words and no paragraphs.

Don't worry, I'll rewrite it again..., it's been almost more than a week, still ubuntu keeps turning off... automatically while i am doing a lot of work!!!

---

