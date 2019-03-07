Device configuration for the Samsung Galaxy Tab A

Copyright (C) 2017 The LineageOS Project
Copyright (C) 2017 Valera Chigir <valera1978@tut.by>

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

------------------------------------------------------------------

* Description

  This repository is for LineageOS on Samsung Galaxy Tab A (gtanotexlwifi)

* How To Build LineageOS for Samsung Galaxy Tab A

  - Make a workspace

mkdir cm16
cd cm16

  - Do repo init & sync

repo init -u git://github.com/LineageOS/android.git -b lineage-16.0

  - Create .repo/local_manifests/roomservice.xml with the following content:

```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>

  <project name="thwalker3/android_device_samsung_gtanotexlwifi" path="device/samsung/gtanotexlwifi" remote="github" revision="los-16.0_64-bsp" />
  <project name="thwalker3/android_kernel_samsung_exynos7870" path="kernel/samsung/exynos7870" remote="github" revision="pie" />
  <project name="thwalker3/android_vendor_samsung_gtanotexlwifi" path="vendor/samsung/gtanotexlwifi" remote="github" />

  <project name="Exynos7870/android_hardware_samsung_slsi-cm_exynos7870" path="hardware/samsung_slsi-cm/exynos7870" remote="github" />
  <project name="Exynos7870/android_hardware_samsung_slsi-cm_exynos" path="hardware/samsung_slsi-cm/exynos" remote="github" />
  <project name="Exynos7870/android_hardware_samsung_slsi-cm_exynos5" path="hardware/samsung_slsi-cm/exynos5" remote="github" />
  <project name="Exynos7870/android_hardware_samsung_slsi-cm_openmax" path="hardware/samsung_slsi-cm/openmax" remote="github" />
  <project name="Exynos7870/android_hardware_samsung" path="hardware/samsung" remote="github" />

</manifest>
```

repo sync

  - Copy proprietary vendor files

  There are two options to to that. Connect your device with adb enabled and run:

./extract-files.sh

  Or if you have the system image unpacked on your disk, then simply run:

    STOCK_ROM_DIR=/path/to/system ./extract-files.sh

  - Setup environment

. build/envsetup.sh

  - Build cm16

brunch gtanotexlwifi
