# build

## Requirement

1. Windows XP,vista,7,8.X,10,11
2. RVCT3.1, Perl
3. MTK MAUI project

## How to make

```
Usage:
  make ["customer"|"mt62xx"] "project" "action" ["modules"]|"file1[ file2[ ...]] | @files"

Description:
  customer   = mtk             (Default customer)
             = firefly17_demo  (FIREFLY17_DEMO project)
             = [mt6217|mt6219|mt6226|mt6227|mt6228|mt6229] (EVB only)
             = ...

  project    = l1s             (Layer 1 stand-alone)
             = gsm             (GSM only)
             = gprs            (GPRS only)
             = umts            (GPRS+UMTS)
             = hspa            (GPRS+UMTS+HSPA)
             = tdd128          (GPRS+TDD128)
             = tdd128dpa       (GPRS+TDD128+HSDPA)
             = tdd128hspa      (GPRS+TDD128+HSPA)
             = basic           (Basic Framework)

  action     = new             (codegen, resgen, clean, update) (default)
             = update or u     (scan, compile, link)
             = slim_update     (scan, compile, link without generating mcddll)
             = remake or r     (compile, link)
             = clean or c      (clean)
             = cci or clean_codegen (clean codegen intermedia files)
             = resgen          (resgen)
             = c,u             (clean then update)
             = c,r             (clean then remake)
             = codegen         (codegen)
             = slim_codegen    (codegen without generating mcddll)
             = mcddll_update   (codegen and generate mcddll)
             = slim_mcddll     (generate mcddll without codegen)
             = viewlog         (open edit to view build log)
             = emigen          (emigen)
             = emiclean        (emiclean)
             = check_dep       (check dependency module(s) after source(s)/header(s) changed)
             = remake_dep      (check_dep, remake)
             = update_dep      (check_dep, update)

  module(s)  = modules' name   (kal, l1, ...)
   => OPTIONAL when action is one of (clean c remake r update u c,r c,u)

  file1      = changed source/header's name (init\include\init.h, ...)
   => VALID ONLY when action is one of (check_dep remake_dep update_dep)
   => MANDATORY when action is one of (check_dep remake_dep update_dep) and @files is NOT specified

  @files     = Specify more changed sources/headers via a file (change list)
   => VALID ONLY when action is one of (check_dep remake_dep update_dep)
   => MANDATORY when action is one of (check_dep remake_dep update_dep) and file1 is NOT specified

Example:
  make gsm new                         (MT6205B EVB new)
  make gprs codegen                    (MT6218B EVB codegen)
  make mt6219 gprs update              (MT6219 EVB update)
  make firefly17_demo gprs new
  make milan_demo gprs c,u init custom
  make mt6219 gprs r init custom drv
  make mt6229 gprs check_dep init\include\init.h
  make mt6229 gprs remake_dep @make\init\init.lis
  make mt6229 gprs update_dep init\src\init.c
```

new building:

```
make HEXING60A_11B GPRS new
```

remake:

```
make HEXING60A_11B GPRS remake
```

e.g. updated the LCD driver:

```
make HEXING60A_11B GPRS remake custom
```