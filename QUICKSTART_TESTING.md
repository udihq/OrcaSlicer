# Quick Start: Download and Test preFlight Features

This is a quick guide to get you testing the new preFlight features in OrcaSlicer as fast as possible.

## ⚡ TL;DR - Quick Start

### Linux (One-Command Build)
```bash
git clone https://github.com/udihq/OrcaSlicer.git && \
cd OrcaSlicer && \
git checkout copilot/merge-athena-wall-generator && \
./build_linux.sh -dsi
# Run: build/src/OrcaSlicer
```

### Windows (Visual Studio 2022)
```powershell
git clone https://github.com/udihq/OrcaSlicer.git
cd OrcaSlicer
git checkout copilot/merge-athena-wall-generator
build_release_vs2022.bat
# Run: build\src\Release\OrcaSlicer.exe
```

### macOS
```bash
git clone https://github.com/udihq/OrcaSlicer.git && \
cd OrcaSlicer && \
git checkout copilot/merge-athena-wall-generator && \
./build_release_macos.sh
# Run: build/OrcaSlicer.app
```

## 🎯 What to Test

### 1. Manual Fan Control (5 minutes)

**Quick Test:**
1. Open OrcaSlicer
2. Print Settings → Advanced → Enable `enable_manual_fan_speeds`
3. Set `manual_fan_speed_external_perimeter` = 100
4. Set `manual_fan_speed_overhang_perimeter` = 80
5. Slice any model with overhangs
6. Check G-code for different fan speeds on different features

**What to Look For:**
- Fan speed changes between features
- Better overhang cooling
- Different speeds visible in G-code comments

### 2. Perimeter Overlap Control (5 minutes)

**Quick Test:**
1. Print Settings → Advanced → `perimeter_perimeter_overlap`
2. Set to 15% (stronger bonding) or -5% (flexible materials)
3. Slice a model with 3+ perimeters
4. Preview → Look at wall cross-section
5. Measure wall spacing

**What to Look For:**
- Visible spacing changes between perimeters
- Stronger/weaker bonding based on overlap

### 3. Athena Wall Generator (2 minutes)

**Quick Test:**
1. Print Settings → Quality → Wall generator → "Athena"
2. Slice any model
3. Check console output

**What to Look For:**
- Warning message about fallback to Classic
- Normal slicing (no errors)
- This feature is safe but not fully active yet

## 📊 Expected Results

| Test | Result | Time |
|------|--------|------|
| Manual Fan Control | ✅ Should work | 5 min |
| Perimeter Overlap | ✅ Should work | 5 min |
| Bridge Overlap | ✅ Should work | 5 min |
| Athena Generator | ⚠️ Safe fallback | 2 min |
| 2-opt Travel | ✅ Automatic | 0 min |

## 🆘 Quick Troubleshooting

**Build Fails?**
- Linux: Run `./build_linux.sh -u` first to install dependencies
- Windows: Install Visual Studio 2022 with C++ tools
- macOS: Install Xcode Command Line Tools

**Can't Find New Settings?**
- Check Print Settings → Advanced mode
- Check Print Settings → Expert mode
- Some settings are in Quality tab

**Athena Not Working?**
- This is expected! Athena shows warning and uses Classic
- Infrastructure is complete but runtime activation is pending
- Safe to test, won't break anything

## 📝 Quick Feedback

After testing (even 5 minutes is helpful!):
1. What features did you test?
2. Did they work as expected?
3. Any crashes or errors?
4. Performance impact?
5. Would you use these features?

Post feedback at: https://github.com/udihq/OrcaSlicer/issues

## 🔗 Full Documentation

For complete details, see: [TESTING_PREFLIGHT_FEATURES.md](TESTING_PREFLIGHT_FEATURES.md)

## ✨ Key Features Summary

- ✅ **Manual Fan Control**: 15 per-feature fan speeds - WORKING
- ✅ **Perimeter Overlap**: Custom bonding strength - WORKING
- ✅ **Bridge Overlap**: Independent bridge control - WORKING
- ⚠️ **Athena Generator**: Infrastructure ready, safe fallback
- ✅ **2-opt Travel**: Automatic path optimization - WORKING

---

**Total Testing Time: ~15 minutes to try main features**

Thank you for helping test! 🙏
