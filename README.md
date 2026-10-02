# Territory Enclosure — сборка APK и EXE/MSI

## Быстрый способ (без установки чего-либо)
1. Создай репозиторий на github.com и загрузи в него всё содержимое этой папки
   (включая скрытую папку `.github`).
2. Открой вкладку **Actions** → дождись зелёной галочки (≈5–10 мин).
3. В запуске внизу, в **Artifacts**, скачай:
   - `territory-apk` → `app-debug.apk` (установка на Android, нужно разрешить «Неизвестные источники»)
   - `territory-windows` → установщик `.exe` (NSIS) и `.msi`

## Локально
- Windows (EXE/MSI): `npm install` → `npm run dist:win` → файлы в `dist/`. Предпросмотр: `npm start`.
- Android (APK): нужны JDK 21 и Android SDK:
  `npm install && npx cap add android && npx capacitor-assets generate --android --assetPath assets && npx cap sync android && cd android && ./gradlew assembleDebug`
  → `android/app/build/outputs/apk/debug/app-debug.apk`

## Примечания
- Иконка вырезана из CbroX.jpg (assets/, build/).
- Игра без интернета запускается (локальный режим); P2P-онлайн и шрифты Google требуют сети.
- APK подписан debug-ключом — для установки вручную подходит, для Google Play нужен release-ключ.
- Установщики Windows не подписаны, поэтому SmartScreen может показать предупреждение.
