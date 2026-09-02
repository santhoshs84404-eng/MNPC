import 'package:flutter/material.dart';

void main() {
  runApp(const MNPCApp());
}

class MNPCApp extends StatelessWidget {
  const MNPCApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Marutam Nelli Polytechnic',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        scaffoldBackgroundColor: const Color(0xFFF4F6F9),
      ),
      home: const MainPage(),
    );
  }
}

class MainPage extends StatefulWidget {
  const MainPage({super.key});

  @override
  State<MainPage> createState() => _MainPageState();
}

class _MainPageState extends State<MainPage> {
  int _currentIndex = 0;

  final List<Widget> _pages = [
    const HomeScreen(),
    const DepartmentsScreen(),
    const TransportScreen(),
    const AdmissionScreen(),
    const ContactScreen(),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('மருதம் நெல்லி பாலிடெக்னிக் கல்லூரி'),
        backgroundColor: const Color(0xFF0D47A1),
      ),
      body: _pages[_currentIndex],
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _currentIndex,
        selectedItemColor: const Color(0xFF0D47A1),
        unselectedItemColor: Colors.grey,
        type: BottomNavigationBarType.fixed,
        onTap: (index) {
          setState(() {
            _currentIndex = index;
          });
        },
        items: const [
          BottomNavigationBarItem(icon: Icon(Icons.home), label: 'முகப்பு'),
          BottomNavigationBarItem(icon: Icon(Icons.school), label: 'துறைகள்'),
          BottomNavigationBarItem(icon: Icon(Icons.directions_bus), label: 'பேருந்து'),
          BottomNavigationBarItem(icon: Icon(Icons.assignment), label: 'சேர்க்கை'),
          BottomNavigationBarItem(icon: Icon(Icons.contact_phone), label: 'தொடர்பு'),
        ],
      ),
    );
  }
}

// ----------------- 1. HOME SCREEN -----------------
class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return SingleChildScrollView(
      padding: const EdgeInsets.all(16.0),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Card(
            elevation: 4,
            shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(12)),
            child: const Padding(
              padding: EdgeInsets.all(16.0),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Text('வரவேற்கிறோம்!', style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold, color: Color(0xFF0D47A1))),
                  SizedBox(height: 8),
                  Text(
                    'மருதம் நெல்லி பாலிடெக்னிக் கல்லூரி (MNPC), பள்ளப்பட்டி, தர்மபுரி-ஒகேனக்கல் நெடுஞ்சாலை. AICTE அங்கீகாரம் மற்றும் தமிழ்நாடு தொழில்நுட்பக் கல்வி இயக்ககத்தின் (DoTE) இணைப்பு பெற்றது.',
                    style: TextStyle(fontSize: 14, height: 1.4),
                  ),
                ],
              ),
            ),
          ),
          const SizedBox(height: 16),
          const Text('முக்கிய செய்திகள் (News & Events)', style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold)),
          const SizedBox(height: 8),
          _buildEventTile('சேர்க்கை 2026 - 2027', 'முதலாமாண்டு மற்றும் நேரடி இரண்டாமாண்டு சேர்க்கை தொடங்கியது.'),
          _buildEventTile('வேலைவாய்ப்பு முகாம் (Placement Day)', '90%-க்கும் அதிகமான மாணவர்களுக்கு முன்னனி நிறுவனங்களில் வேலைவாய்ப்பு.'),
          _buildEventTile('FM மருதம் நெல்லி 89.6', 'கல்லூரியின் சமூக வானொலி சேவை இயங்குகிறது.'),
        ],
      ),
    );
  }

  static Widget _buildEventTile(String title, String desc) {
    return Card(
      child: ListTile(
        leading: const Icon(Icons.campaign, color: Colors.orange),
        title: Text(title, style: const TextStyle(fontWeight: FontWeight.bold)),
        subtitle: Text(desc),
      ),
    );
  }
}

// ----------------- 2. DEPARTMENTS SCREEN -----------------
class DepartmentsScreen extends StatelessWidget {
  const DepartmentsScreen({super.key});

  final List<String> departments = const [
    'Electrical & Electronics Engineering (EEE)',
    'Electrical Engineering & EV Technology',
    'Mechanical Engineering',
    'Civil Engineering',
    'Agricultural Engineering',
    'Computer Engineering',
    'Artificial Intelligence & Machine Learning',
    'Electronics & Communication Engineering',
    'Medical Laboratory Technology',
    'Basic Engineering (I-Year)'
  ];

  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      padding: const EdgeInsets.all(16.0),
      itemCount: departments.length,
      itemBuilder: (context, index) {
        return Card(
          child: ListTile(
            leading: const Icon(Icons.engineering, color: Color(0xFF0D47A1)),
            title: Text(departments[index], style: const TextStyle(fontWeight: FontWeight.w600)),
            trailing: const Icon(Icons.arrow_forward_ios, size: 16),
          ),
        );
      },
    );
  }
}

// ----------------- 3. TRANSPORT SCREEN -----------------
class TransportScreen extends StatelessWidget {
  const TransportScreen({super.key});

  final List<String> busRoutes = const [
    'பிக்கிலி (Pikkili)',
    'வத்தலாபுரம் (Vathalapuram)',
    'இராயக்கோட்டை (Rayakottai)',
    'கம்பைநல்லூர் (Kambainallur)',
    'போச்சம்பள்ளி (Pochampalli)',
    'காவேரிப்பட்டினம் (Kaveripattinam)',
    'அஞ்செட்டி (Anchetty)',
    'பஞ்சப்பள்ளி (Panchappalli)',
    'நெருப்பூர் (Neruppur)',
    'மொரப்பூர் (Morappur)'
  ];

  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      padding: const EdgeInsets.all(16.0),
      itemCount: busRoutes.length,
      itemBuilder: (context, index) {
        return Card(
          child: ListTile(
            leading: const Icon(Icons.directions_bus, color: Colors.green),
            title: Text(busRoutes[index]),
          ),
        );
      },
    );
  }
}

// ----------------- 4. ADMISSION SCREEN -----------------
class AdmissionScreen extends StatelessWidget {
  const AdmissionScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(16.0),
      child: ListView(
        children: [
          const Text('சேர்க்கை விண்ணப்பம் (Admission Enquiry)', style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold)),
          const SizedBox(height: 16),
          const TextField(decoration: InputDecoration(labelText: 'மாணவர் பெயர்', border: OutlineInputBorder())),
          const SizedBox(height: 12),
          const TextField(decoration: InputDecoration(labelText: 'கைபேசி எண்', border: OutlineInputBorder()), keyboardType: TextInputType.phone),
          const SizedBox(height: 12),
          const TextField(decoration: InputDecoration(labelText: 'விரும்பும் படிப்பு (Department)', border: OutlineInputBorder())),
          const SizedBox(height: 16),
          ElevatedButton(
            style: ElevatedButton.styleFrom(backgroundColor: const Color(0xFF0D47A1), padding: const EdgeInsets.symmetric(vertical: 14)),
            onPressed: () {},
            child: const Text('விண்ணப்பிக்கவும்', style: TextStyle(fontSize: 16, color: Colors.white)),
          )
        ],
      ),
    );
  }
}

// ----------------- 5. CONTACT SCREEN -----------------
class ContactScreen extends StatelessWidget {
  const ContactScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(16.0),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: const [
          Text('தொடர்பு கொள்ள', style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold, color: Color(0xFF0D47A1))),
          SizedBox(height: 16),
          ListTile(leading: Icon(Icons.location_on), title: Text('பள்ளப்பட்டி, தர்மபுரி நெடுஞ்சாலை, தர்மபுரி - 636803')),
          ListTile(leading: Icon(Icons.phone), title: Text('+91 97888 53001 / 04342 242422')),
          ListTile(leading: Icon(Icons.email), title: Text('info@marutamnelli.com')),
        ],
      ),
    );
  }
}
