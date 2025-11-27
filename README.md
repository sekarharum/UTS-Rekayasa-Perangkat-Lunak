UTS Rekayasa Perangkat Lunak

Judul Studi Kasus: Sistem Monitoring di PT. APL

Deskripsi Singkat Sistem

Sistem Monitoring di PT. APL digunakan untuk memantau aktivitas operasional harian, kondisi mesin, dan laporan dari operator lapangan. Sistem ini membantu supervisor dan manajemen dalam melakukan pengawasan, verifikasi laporan, serta pengambilan keputusan berbasis data.

Aktor dalam Sistem

1. Operator Lapangan – Menginput laporan monitoring.


2. Supervisor – Memverifikasi laporan dan memberikan status.


3. Admin Sistem – Mengelola pengguna dan pengaturan sistem.


4. Manajemen – Melihat rekap laporan untuk evaluasi.



Use Case Utama

Login pengguna

Input laporan monitoring

Verifikasi laporan

Melihat laporan dan rekap

Pengelolaan data dan pengguna


Class Diagram (Deskripsi Kelas)

Kelas Utama:

User (userId, username, password, role)

MonitoringReport (reportId, operatorId, mesinId, tanggal, waktu, deskripsi, status)

Machine (machineId, namaMesin, lokasi, status)

Verification (verificationId, reportId, supervisorId, statusVerifikasi, catatan)

Notification (notifId, userId, pesan, waktu)


Relasi antar kelas:

Satu User dapat membuat banyak MonitoringReport.

MonitoringReport terhubung dengan Machine.

Verification terhubung ke MonitoringReport.

Notification ditujukan kepada User.


Penerapan Prinsip SOLID

SRP: MonitoringReport hanya menangani data laporan.

OCP: Sistem dapat diperluas tanpa mengubah struktur kelas utama.

LSP: Subclass seperti Admin dapat menggantikan User tanpa mengubah perilaku sistem.

ISP: Interface dipisah antara input laporan dan verifikasi laporan.

DIP: Modul notifikasi menggunakan abstraksi sehingga bisa diganti email/WA tanpa ubah logika inti.


Sequence Diagram (Deskripsi Alur)

Input Laporan oleh Operator

1. Operator login.


2. Sistem memverifikasi kredensial.


3. Operator membuka menu input laporan.


4. Operator mengisi laporan monitoring.


5. Sistem menyimpan laporan.


6. Sistem mengirim notifikasi ke supervisor.



Verifikasi oleh Supervisor

1. Supervisor menerima notifikasi laporan baru.


2. Supervisor membuka laporan.


3. Supervisor menentukan status (approved/rejected).


4. Sistem memperbarui status laporan.


5. Sistem mengirim notifikasi ke operator.



State Machine (MonitoringReport)

Draft → laporan dibuat

Submitted → laporan dikirim operator

Reviewed → diperiksa supervisor

Approved / Rejected → keputusan supervisor

Archived → selesai dan disimpan


Analisis Risiko

Server mengalami downtime sehingga menghambat monitoring.

Operator salah input data.

Risiko keamanan seperti akses tanpa izin.


Non-Functional Requirements

Keamanan: autentikasi terenkripsi, role based access.

Reliability: sistem berjalan 24/7.

Usability: tampilan sederhana untuk operator.

Performance: waktu akses < 2 detik per halaman.

Scalability: mudah ditambah modul baru.
