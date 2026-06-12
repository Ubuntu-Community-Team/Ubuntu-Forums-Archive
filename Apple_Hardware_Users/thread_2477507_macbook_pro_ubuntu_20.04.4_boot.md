---
title: "macbook pro ubuntu 20.04.4 boot"
date: 2022-07-27
forum: Apple Hardware Users
---

### Post by horizon992 on 2022-07-27
Hello,

Until recently my quite old macbook pro...
 
Intel® Core&#8482; i5-3210M CPU @ 2.50GHz × 4 
Intel® HD Graphics 4000 (IVB GT2)
Ubuntu 20.04.4 LTS only 

...was working fine, if a little hot and slow to boot (bright white screen)

I now get the following message before the Ubuntu desktop appears:

    ```
[ 0.0791011 DMAR-IR: [Firmware Bug]: ioapic 2 has no mapping iommu, interrupt remapping will be disabled [COLOR=#212121] [ 0.156165] ACPI Error: Needed type [Reference], found [Integer] 00000000f956

  b00a (20210730/exresop-66)

  [ 0.1561751 ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [St ore] (20210730/dswexec-431)

  [ 0.1561981 ACPI Error: Aborting method PR.CPUO. PDC due to previous error (AE_AML_OPERAND_TYPE) (20210730/psparse-529)

  /dev/sda2: clean, 300962/30498816 files, 9495857/121965056 blocks
[/COLOR]
    
  
```

So this looks like a BIOS issue and at this point I'm lost. So any advice on how to resolve this would be greatly appreciated.

horizon99

---

### Post by QIII on 2022-07-27
Moved to Apple Hardware Users as a more appropriate sub-forum.

---

### Post by Joel_Schrock on 2022-09-17
I have what seems to be the same problem. The text I have gotten is only a little different:

```
[0.134018] DMAR-IR: [Firmware Bug]: ioapic 2 has no mapping iommu, interrupt remapping will be disabled
[0.222946] ACPI Error: Needed type [Reference], found [Integer] 00000000936362c9 (20210730/exresop-66)
[0.222956] ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20210730/dswexec-431)
[0.222976] ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERND_TYPE) (20210730/psparse-529)
```

And then all I get is a flashing cursor with which I can do nothing.

---

